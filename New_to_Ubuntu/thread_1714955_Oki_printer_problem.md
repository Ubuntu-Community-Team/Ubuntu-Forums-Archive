---
title: "Oki printer problem"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by wepxc11 on 2011-03-26
I have downloaded the driver for my oki 24 pin dotmatrix printer from the oki web site but can not get it to run. The "rastertookidotmatrix" file needs to be in the usr/lib/cups/filter folder but i am unable to get it to cut and copy from the download folder because i do not have the correct permission.
can you tell me how to move this file to the correct place please.

---

### Post by jtarin on 2011-03-26
Can you right-click on the folder and choose to open as administrator? This will open an administrators Nautilus and do your work from there. If  so, then proceed with your copy and paste. If you do not have the right-click option from a terminal issue the command ```
sudo nautilus
```

---

### Post by wepxc11 on 2011-03-27
tried to do as suggested but had to use the sudo nautilus command to move file and now getting "has insecure permissions 0100777"
and "oki cups insecure filter"
have deleted all files and downloaded driver again but still fails the same. What am i doing wrong? 
ps the driver is coming from the oki web site and is for an oki ML390 24 pin printer

---

### Post by gordintoronto on 2011-03-27
Just as a comment, you don't have a printer problem, you have a file permissions problem. Somebody who knows all about Oki printers might not be able to help you.

What were you trying to do when you got the "has insecure permissions 0100777" error?

---

### Post by jtarin on 2011-03-27
Try ```
chmod 555
``` to the file /usr/lib/cups/filter/
Then you need to restart cups.
You can make sure that the error is gone by checking [http://localhost:631/printers](http://localhost:631/printers)

---

### Post by wepxc11 on 2011-03-28
tried to change permissions using chmod 555 /usr/lib/cups/filter but got the reply "operation not permitted"
there seems to be two methods of installing this printer. the first by the install file that comes with the download and the add a printer method on Ubunto neither seem to work 
below is the install file that comes with the download should i be using this or the add printer method?


```
#!/bin/sh
#############################################################
# Copyright 2010 Oki Data Corporation
#############################################################
# install PPD and/or filter
#############################################################
# version: 2.0
#############################################################

PATH=/bin:/usr/sbin:/usr/bin
export PATH

CP="/bin/cp"
CHMOD="/bin/chmod"
CHOWN="/bin/chown"
CUT="/usr/bin/cut"
ECHO="/bin/echo"
GREP="/bin/grep"
MKDIR="/bin/mkdir"

programName="install.sh"
OKI_FILTER="rastertookidotmatrix"

#####################################################
# generic copy 
#####################################################
copy_stuff()
{
    if [ -f "${2}/${1}" ] ; then
        ${ECHO} "${programName}: WARNING: ${2}/${1} already exist."
        return
    fi

    ${CHOWN} root ${1} > /dev/null 2>&1
    if [ $? -ne 0 ] ; then
        ${ECHO} "${programName}: WARNING: cannot change owner - ${1}."
    fi

    ${CP} "${1}" "${2}" > /dev/null 2>&1
    if [ $? -ne 0 ] ; then
        error_msg "cannot copy ${1}."
    fi

}

#####################################################
# error routine
#####################################################
error_msg()
{
    ${ECHO} "${programName}: ERROR: ${1}"
    exit 1
}

#####################################################
# change mode
#####################################################
chg_mode() 
{ 
    ${CHMOD} "${1}" "${2}"  > /dev/null 2>&1
    if [ $? -ne 0 ] ; then
        ${ECHO} "${programName}: WARNING: cannot change mode - ${2}"
    fi
}


if [ `id -u` -ne 0 ] ; then
    ${ECHO}  "${programName}: ERROR: must be root"
    exit 1
fi

_CUPS="/etc/init.d/cups"
_CUPSD="/etc/init.d/cupsd"
_CUPSYS="/etc/init.d/cupsys"

########################
# paths . . .
########################
PPD_PATH="/usr/share/ppd"
CUPSPPD_PATH="/usr/share/cups/model"
_PPD_PATH=""
CUPSFILTER_PATH="/usr/lib/cups/filter"

if [ -x ${CUPSPPD_PATH} ] ; then
    _PPD_PATH="${CUPSPPD_PATH}"
elif [ -x ${PPD_PATH} ] ; then
    _PPD_PATH="${PPD_PATH}"
fi

_PPD_PATH="${_PPD_PATH:-${CUPSPPD_PATH}}"

for i in `ls ok*ppd*`
do
    ## permissions ##
    chg_mode 444 ${i}

    ## copy PPDs ##
    copy_stuff ${i} ${_PPD_PATH}
done

if [ ! -x ${OKI_FILTER} ] ; then
    error_msg "cannot find ${OKI_FILTER}"
fi

## permissions ##
chg_mode 555 ${OKI_FILTER}

## copy filter ##
copy_stuff ${OKI_FILTER} ${CUPSFILTER_PATH}

for i in ${_CUPS} ${_CUPSD} ${_CUPSYS}
do
    ${i} restart  > /dev/null 2>&1
done

${ECHO} "INFO: ${programName} completed . . ."

exit 0
```

---

### Post by jtarin on 2011-03-28
Whenever an operation won't complete with this error try prefacing the command with "sudo".```
sudo chmod 555 /usr/lib/cups/filter
```root is the owner only root can change.Look at your script.....you must be root to execute the script.

---

### Post by wepxc11 on 2011-03-29
I'm terribly sorry but i thought i could find out how to restart cups but i obviously got the wrong command. could you give me the command to restart cups please.

---

### Post by jtarin on 2011-03-29
> **wepxc11 said:**
> I'm terribly sorry but i thought i could find out how to restart cups but i obviously got the wrong command. could you give me the command to restart cups please.```
sudo /etc/init.d/cupsys restart
```

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html)

---

### Post by wepxc11 on 2011-04-02
Not getting anywhere with this. i will have another go tomorrow and if it fails again i will send all the details and the driver files for checking.

---

### Post by jtarin on 2011-04-02
> Not getting anywhere with this. i will have another go tomorrow and if it fails again i will send all the details and the driver files for checking. It would be helpful if we knew specifically what your referring to, at this point.Cups restart????? What is the exact model of your printer?
I'm linking you to the[ Linux Foundation Workgroup on Foomatic]("http://www.linuxfoundation.org/collaborate/workgroups/openprinting/databasefoomatic#Using_Foomatic_with_a_particular_printer_and_spooler").....My advice is to read about Foomatic and  go through the linked  documentation for 
CUPS. Once you have done this and have a better understanding of CUPS, filters and PPD's you will then be able to see how effortless it can be to setup a supported printer. I'm not saying you don't need your drivers you downloaded but this will clarify a multitude of things and save you time waiting on answers in the forum. Of course at any point you don't understand something post back. I was like you lost in the whole process at one time and with my Windows mentality it only made it more difficult.

---

### Post by wepxc11 on 2011-04-03
Thank you for your reply. I will study the link this evening.
This morning i had another go at the printer (its an OKI ML390 24 pin printer) by deleting and reloading it but still getting "insecure permissions 010077" and "cups insecure filter" but i then deleted the printer and reinstated it as the oki 24 pin default  that is on the Ubuntu driver list and the printer started to print rubbish but i got no error messages so it must be down to the drivers i'm trying to load. just a matter of finding where.

---

