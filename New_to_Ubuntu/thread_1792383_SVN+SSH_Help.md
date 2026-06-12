---
title: "SVN+SSH Help"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by H3110 on 2011-06-28
Hey,

I'm having an issue with the **svn+ssh://** feature on Ubuntu/SubVersion. Basically I have a bash script which will be executed to checkout the repository to a development environment.

1. I have the bash script 99% working, the problem is i cannot auotmatically login to SSH for instance:

```
sudo svn checkout svn+ssh://serv.com/var/svn/repo /var/www/site.com/dev --username user --password 'test$$'
```

I've read upon a "bug" with the --username not being the SSH username, and the following works (**except the password**)

```
sudo svn checkout svn+ssh://user@serv.com/var/svn/repo /var/www/site.com/dev --password 'test$$'
```

How can i get the password to automatically login (and not prompt me).

2. The process - This is how it will be executed!

-> User commits SVN changes.
-> SVN Post-commit-hook executes /var/bin/svn_checkout (via PHP/CGI).
-> Bash executes checkout
-> Complete

3. The bash script is as follows:

```
#!/bin/bash -x
# -=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
# Checkout repository
# -=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

usage()
{
cat << EOF
usage: $0 options

This script will checkout a repository to development.

OPTIONS:
   -s   The site/repository.
   -u   The SSH Username.
   -p   The SSH Password.
EOF
}

if [ "$1" == "?" ]; then
        usage
        exit
fi

# -=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

SH_DIR_DEV="/var/www/"
SH_DIR_SVN="/var/svn/"

# -=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

while getopts ":s:u:p:" OPT; do
        case ${OPT} in
                s) DOMAIN_NAME=${OPTARG} ;;
                u) USER_NAME=${OPTARG} ;;
                p) USER_PWD=${OPTARG} ;;
                *)
                        echo "Invalid option: -${OPT} ${OPTARG}"
                        exit 1
                ;;
        esac
done

if [[ -z "${DOMAIN_NAME}" ]] || [[ -z "${USER_NAME}" ]] || [[ -z "${USER_PWD}" ]]; then
        usage
        exit
fi

if [ ! -e "${SH_DIR_DEV}${DOMAIN_NAME}" ]; then
        echo "Domain name ${DOMAIN_NAME} does not exist, aborting."
        exit
fi

echo "Checking out repository..."
CMD="svn checkout --password '${USER_PWD}' svn+ssh://${USER_NAME}@server.com${SH_DIR_SVN}${DOMAIN_NAME} ${SH_DIR_DEV}${DOMAIN_NAME}/dev"
eval CMD

echo "Updating ownership and mode..."
chown -R www-data:www-data ${SH_DIR_DEV}${DOMAIN_NAME}/dev

echo "Clearing cache directories..."
rm -fr `find ${SH_DIR_DEV}${DOMAIN_NAME}/dev -type d -name .svn`
```

Any help would be very much appreciated!

Thanks.

---

