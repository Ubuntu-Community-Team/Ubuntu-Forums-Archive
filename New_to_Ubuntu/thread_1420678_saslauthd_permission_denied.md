---
title: "saslauthd permission denied"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by rosegal on 2010-03-03
hello thr...

m trying to install postfix..and was successful but i got stuck again when i was trying to configure saslauthd..everytime i start the saslauthd i get the result as shown below..

root@xxxx-laptop:/home/xxxx# /etc/init.d/saslauthd start
bash: /etc/init.d/saslauthd: Permission denied

this is my /etc/init.d/saslauthd :

**************************************************************************************

#!/bin/sh -e

NAME=saslauthd
DAEMON="/usr/sbin/${NAME}"
DESC="SASL Authentication Daemon"
DEFAULTS=/etc/default/saslauthd

test -f "${DAEMON}" || exit 0

# Source defaults file; edit that file to configure this script.
if [ -e "${DEFAULTS}" ]; then
    . "${DEFAULTS}"
fi

# If we're not to start the daemon, simply exit
if [ "${START}" != "yes" ]; then
    exit 0
fi

# If we have no mechanisms defined
if [ "x${MECHANISMS}" = "x" ]; then
    echo "You need to configure ${DEFAULTS} with mechanisms to be used"
    exit 0
fi

# Add our mechanimsms with the necessary flag
for i in ${MECHANISMS}; do
    PARAMS="${PARAMS} -a ${i}"
done

# Consider our options
case "${1}" in
  start)
        echo -n "Starting ${DESC}: "
        ln -fs /var/spool/postfix/var/run/${NAME} /var/run/${NAME}
        ${DAEMON} ${PARAMS}
        echo "${NAME}."
        ;;
  stop)
        echo -n "Stopping ${DESC}: "
        PROCS=`ps aux | grep -iw '/usr/sbin/saslauthd' | grep -v 'grep' |awk '{print $2}' | tr '\n' ' '`
        if [ "x${PROCS}" != "x" ]; then        
          kill -15 ${PROCS} &> /dev/null
        fi
        echo "${NAME}."
        ;;
  restart|force-reload)
        $0 stop
        sleep 1
        $0 start
        echo "${NAME}."
        ;;
  *)
        echo "Usage: /etc/init.d/${NAME} {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0

**************************************************************************************
any idea why i am getting this??..

---

### Post by Jefferythewind on 2010-03-03
try:

```
sudo /etc/init.d/saslauthd start
```

---

### Post by rosegal on 2010-03-03
i used and it says command not found..neway why must i put sudo when i am already in root...

root@xxxx-laptop:/home/xxxx# sudo /etc/init.d/saslauthd start
sudo: /etc/init.d/saslauthd: command not found

???

---

### Post by Jefferythewind on 2010-03-03
usually I get the permission denied message when I need root privileges but have not used the sudo command.  I am the root user of my computer but I still have to use sudo to enable root user privileges at the command line.  However, this is a setting that you can change, so that you have super user privileges for the whole time you are logged in.  Sorry I couldn't of more help.

---

### Post by Penguin Guy on 2010-03-03
Perhaps the execution flag is not set?
As root, try: 
```

chmod +x /etc/init.d/saslauthd
/etc/init.d/saslauthd start

```

---

### Post by rosegal on 2010-03-05
hey thr..i have tried using d command u gv..there was no change though so i assume its working..i proceeded to another step which is telneting..but gt stuck again as usual..

Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

it just stopped here..i cant proceed anything after this again..i check the mail daemon and got this errors :

Mar  5 13:39:50 royth-laptop postfix/master[2495]: warning: process /usr/lib/postfix/smtpd pid 6413 exit status 1
Mar  5 13:39:50 royth-laptop postfix/master[2495]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

any idea as a solution...
pls help me!!!!!!!!!!!

---

