AC_PREREQ([2.60])
AC_INIT([phpplatesender],[1.0.0],,)
AC_CONFIG_AUX_DIR([.])
AM_INIT_AUTOMAKE([foreign])
#AC_CONFIG_MACRO_DIR([m4])

# Checks for programs.

AC_PROG_INSTALL

AC_PATH_PROG([CURL_BINARY_PATH],[curl],[no])
if test "x$CURL_BINARY_PATH" == "xno"; then
    AC_MSG_ERROR([Curl binary is missing, please install it])
fi
AC_SUBST(CURL_BINARY_PATH)

AC_PATH_PROG([PHPCLI_BINARY_PATH],[php],[no])
if test "x$HAVE_PHPCLI_BINARY" == "xno"; then
    AC_MSG_ERROR([PHP client binary is missing, please install it])
fi
AC_SUBST(PHPCLI_BINARY_PATH)

# Options

PHPMAILER_EXT_DIR=
PHPMAILER_FILE=
AC_ARG_WITH(phpmailerdir,
    [  --with-phpmailerdir=<path>    prefix of directory for the phpmailer
                                     library],
    [PHPMAILER_EXT_DIR=$with_phpmailerdir],
    AC_MSG_WARN([You can call configure with the --with-phpmailerdir option.
    This tells configure to not install phpmailer but use the given directory
    at runtime to load this library.
    e.g. --with-phpmailerdir=/usr/share/php/libphp-phpmailer])
)
if test "x$PHPMAILER_EXT_DIR" = "x"; then
    PHPMAILER_FILE=vendor/phpmailer/phpmailer/class.phpmailer.php
fi
AC_SUBST(PHPMAILER_EXT_DIR)
AC_SUBST(PHPMAILER_FILE)

PHEANSTALK_EXT_DIR=
PHEANSTALK_FILE=
AC_ARG_WITH(pheanstalkdir,
    [  --with-pheanstalkdir=<path>   prefix of directory for the pheanstalk
                                     library],
    [PHEANSTALK_EXT_DIR=$with_pheanstalkdir],
    AC_MSG_WARN([You can call configure with the --with-pheanstalkdir option.
    This tells configure to not install pheanstalk but use the given directory
    at runtime to load this library.
    e.g. --with-pheanstalkdir=/usr/share/php/php-pheanstalk])
)
if test "x$PHEANSTALK_EXT_DIR" = "x"; then
    PHEANSTALK_FILE=vendor/pda/pheanstalk/pheanstalk_init.php
fi
AC_SUBST(PHEANSTALK_EXT_DIR)
AC_SUBST(PHEANSTALK_FILE)

RUN_DIR=/var/run/phpplatesender
AC_ARG_WITH(rundir,
    [  --with-rundir=<path>          prefix of directory for the process file,
                                     default /var/run/phpplatesender],
    [RUN_DIR=$with_rundir],
    AC_MSG_WARN([You can call configure with the --with-rundir option.
    This tells phpplatesender where to write the process file.
    e.g. --with-rundir=/var/run/phpplatesender])
)
AC_SUBST(RUN_DIR)

LOG_DIR=/var/log/phpplatesender
AC_ARG_WITH(logdir,
    [  --with-logdir=<path>          prefix of directory for the log file,
                                     default /var/log/phpplatesender],
    [LOG_DIR=$with_logdir],
    AC_MSG_WARN([You can call configure with the --with-logdir option.
    This tells phpplatesender where to write the log file.
    e.g. --with-logdir=/var/log/phpplatesender])
)
AC_SUBST(LOG_DIR)

CONFIG_DIR=/etc/phpplatesender
AC_ARG_WITH(confdir,
    [  --with-confdir=<path>         prefix of directory for the config file,
                                     default /etc/phpplatesender],
    [CONFIG_DIR=$with_confdir],
    AC_MSG_WARN([You can call configure with the --with-confdir option.
    This tells phpplatesender where to look for the configuation file.
    e.g. --with-confdir=/etc/phpplatesender])
)
AC_SUBST(CONFIG_DIR)

IMAGE_DIR=/var/lib/openalpr/plateimages
AC_ARG_WITH(imagedir,
    [  --with-imagedir=<path>        prefix of alprd directory for images,
                                     default /var/lib/openalpr/plateimages],
    [IMAGE_DIR=$with_imagedir],
    AC_MSG_WARN([You can call configure with the --with-imagedir option.
    This tells phpplatesender where to look for images of detected plates.
    e.g. --with-imagedir=/var/lib/openalpr/plateimages])
)
AC_SUBST(IMAGE_DIR)

WEB_USER=apache
AC_ARG_WITH(webuser,
    [  --with-webuser=<user>         name of web user, default apache],
    [WEB_USER=$with_webuser],
    AC_MSG_WARN([You can call configure with the --with-webuser option.
    This tells configure what the user name of the web user is if it is not the
    default of 'apache'.
    e.g. --with-webuser=apache or --with-webuser=web])
)
AC_SUBST(WEB_USER)

WEB_GROUP=apache
AC_ARG_WITH(webgroup,
    [  --with-webgroup=<group>       name of web group, default apache],
    [WEB_GROUP=$with_webgroup],
    AC_MSG_WARN([You can call configure with the --with-webgroup option.
    This tells configure what the group name of the web group is if it is not
    the default of 'apache'.
    e.g. --with-webgroup=apache or --with-webgroup=web])
)
AC_SUBST(WEB_GROUP)

AC_CONFIG_FILES([Makefile lang/Makefile config.php default.php])

AC_OUTPUT