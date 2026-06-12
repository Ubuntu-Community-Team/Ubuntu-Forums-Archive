---
title: "Running .bat file"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by atulmittal_mds on 2011-04-13
Hi All,

I am new to this community..
Can anyone help me in understanding how do i run a batch file in Ubuntu..Actually i have already make an .bat file in which i have written some Oracle scripts like creating and inserting.. Since i am using ubuntu first time so i wont be able to run this batch file...
Hope I would get some better experience in first time..

Thanks 

Cheers 
Atul

---

### Post by crispy_420 on 2011-04-13
Thought .bat was for Windows.

---

### Post by earthpigg on 2011-04-13
In the unix/linux world, we have shell scripts. by convention, they commonly end in .sh instead of .bat and contain bash commands instead of DOS commands.

share with us what these .bat files are?

---

### Post by atulmittal_mds on 2011-04-13
.bat file content 


@echo OFF
echo Welcome to the DB install and update utility for OneView.
set /P dbuser=Enter DB user name :
set /P dbpswd=Enter DB password  :
set /p dbname=Enter DB Name/SID  :

echo Connecting to the Database..
@echo off
SETLOCAL

echo deleting previous logs if any

del %temp%\OVOraDBInstall*.log

set NLS_LANG=AMERICAN_AMERICA.WE8MSWIN1252

SQLPLUS.exe -S -L  %dbuser%/%dbpswd%@%dbname% @1.1\Oracle\1.sql 
SQLPLUS.exe -S -L  %dbuser%/%dbpswd%@%dbname% @1.3\Oracle\1.sql 
SQLPLUS.exe -S -L  %dbuser%/%dbpswd%@%dbname% @1.4\Oracle\1.sql 
SQLPLUS.exe -S -L  %dbuser%/%dbpswd%@%dbname% @1.5\Oracle\1.sql 
SQLPLUS.exe -S -L  %dbuser%/%dbpswd%@%dbname% @1.6\Oracle\1.sql 
SQLPLUS.exe -S -L  %dbuser%/%dbpswd%@%dbname% @1.7\Oracle\1.sql 
SQLPLUS.exe -S -L  %dbuser%/%dbpswd%@%dbname% @1.8\Oracle\1.sql 
SQLPLUS.exe -S -L  %dbuser%/%dbpswd%@%dbname% @1.9\Oracle\1.sql 
SQLPLUS.exe -S -L  %dbuser%/%dbpswd%@%dbname% @1.10\Oracle\1.sql

echo DB install and update utility for OneView has finished execution. 
echo merging log files

copy %temp%\OVOraDBInstall*.log %temp%\OVOraDBInstall.log
echo Log file for the session can be found at %temp%\OVOraDBInstall.log
pause

---

### Post by deconstrained on 2011-04-13
You might have luck running the batch file with Wine (a DOS compatibility layer that allows some Windows programs to run in Unix environments), but it's not guaranteed to work.

---

### Post by Karlchen on 2011-04-13
Hello, atulmittal_mds.

Here is a rough translation of your .cmd script (Windows) into .sh script (Linux using bash as its shell). No warranty is given that the script will do what you expect it to do. I have got no way of making sure that all the prerequisites are met which will make sure that the script can run properly.
```
#!/bin/bash
#
echo "Welcome to the DB install and update utility for OneView."
echo "Enter DB user name : \c"
read DBUSER
echo "Enter DB password : \c"
read DBPSWD
echo "Enter DB Name/SID : \c"
read DBNAME

echo "Connecting to the Database.."
echo "deleting previous logs if any"
rm $TMP/OVOraDBInstall*.log > /dev/null 2>&1

export NLS_LANG=AMERICAN_AMERICA.WE8MSWIN1252

sqlplus  -S -L $DBUSER/$DBPSWD@$DBNAME @1.1/Oracle/1.sql
sqlplus  -S -L $DBUSER/$DBPSWD@$DBNAME @1.3/Oracle/1.sql
sqlplus  -S -L $DBUSER/$DBPSWD@$DBNAME @1.4/Oracle/1.sql
sqlplus  -S -L $DBUSER/$DBPSWD@$DBNAME @1.5/Oracle/1.sql
sqlplus  -S -L $DBUSER/$DBPSWD@$DBNAME @1.6/Oracle/1.sql
sqlplus  -S -L $DBUSER/$DBPSWD@$DBNAME @1.7/Oracle/1.sql
sqlplus  -S -L $DBUSER/$DBPSWD@$DBNAME @1.8/Oracle/1.sql
sqlplus  -S -L $DBUSER/$DBPSWD@$DBNAME @1.9/Oracle/1.sql
sqlplus  -S -L $DBUSER/$DBPSWD@$DBNAME @1.10/Oracle/1.sql

echo "DB install and update utility for OneView has finished execution."
echo "merging log files"

cat $TMP/OVOraDBInstall*.log > $TMP/OVOraDBInstall.log
echo "Log file for the session can be found at $TMP/OVOraDBInstall.log"
echo "Press the ANY key to continue \c"
read ANSW

```And keep in mind that Linux is case sensitive.

HTH,
Karl

---

### Post by atulmittal_mds on 2011-04-13
Hey thanks a lot [COLOR="Blue"][FONT="Arial Black"]karl[/FONT][/COLOR]..yes your translated file content works for me..
This was my first Post and i got really a wonderful help...I m very happy with your solution..
Thanks again Karl..:):)

---

### Post by earthpigg on 2011-04-13
ya i gotta say Karlchen, that was pretty above and beyond the all of duty.

---

### Post by Karlchen on 2011-04-14
Hi, guys.

De nada. :smile:

Karl

---

