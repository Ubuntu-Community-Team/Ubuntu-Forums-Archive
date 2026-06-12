---
title: "Run SVN post commit hook as root."
date: 2011-07-02
forum: New to Ubuntu
---

### Post by H3110 on 2011-07-02
I've been waiting a while for some help with this topic - I thought it would be best to re-write the question.


I have a website hosted in: /var/www/domain.com/
I have an SVN repository: /var/svn/domain.com/
I have an SVN post-commit hook: /var/svn/hooks.d/post-commit


A symbolic link has been set-up to direct each svn repository to the ../hooks.d/ directory.


/var/svn/hooks.d/post-commit*
```
#!/bin/bash
su -c /var/bin/svn_co -h $1 >> /var/log/subversion.log
```


/var/bin/svn_co*
```
#!/bin/bash
# -=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
# Checkout repository to development environment 
# -=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

usage()
{
cat << EOF
usage:

Checkout a virtual host SVN repository to the development environment,
removing all traces of .svn cache directories afterwards.

./svn_co -h <domain_name>

OPTIONS:
	-h <domain_name>	The virtual host domain name.
EOF
}

# -=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

SH_DIR_DEV="/var/www/"
SH_DIR_SVN="/var/svn/"

# -=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

if [ "$1" == "--help" ]; then
	usage
	exit
else
	while getopts ":h:" OPT; do
		case ${OPT} in
			h) DOMAIN_NAME=`echo ${OPTARG} | cut -d '.' -f 2-` ;;
			*)
				echo "Invalid option: -${OPT} ${OPTARG}"
				echo "Use: --help for more information."
				exit 1
			;;
		esac
	done
fi

if [ -z "${DOMAIN_NAME}" ]; then
	usage
	exit
fi

if [ ! -e "${SH_DIR_DEV}${DOMAIN_NAME}" ]; then
	echo "Domain name ${DOMAIN_NAME} does not exist, aborting."
	exit
fi

echo "Checking out repository..."
svn export --force file://${SH_DIR_SVN}${DOMAIN_NAME} ${SH_DIR_DEV}${DOMAIN_NAME}/dev

echo "Updating ownership and mode..."
chown -R www-data:www-data ${SH_DIR_DEV}${DOMAIN_NAME}/dev

echo "Clearing cache directories..."
rm -fr `find ${SH_DIR_DEV}${DOMAIN_NAME}/dev -type d -name .svn`
```


/var/log/subversion.log
```
Usage: su [options] [LOGIN]
```


Wondering if someone could help me?
Thanks

---

