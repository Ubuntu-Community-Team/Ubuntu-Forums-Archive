---
title: "how to run .bat file"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by atulmittal_mds on 2011-04-18
Hi all,

can anyone help me what changes should i need to do in this mysql.bat file in order to run it on ubuntu..

---

### Post by samvkampen on 2011-04-18
Do you want to have a similar thing to run in Ubuntu, or want to just look if it works?
If you just want to look if it works, and nothing more, I suggest installing [WINE (**LINK**)]("http://winehq.org"). Otherwise, I can't help you, sorry.

---

### Post by d3v1150m471c on 2011-04-18
.bat is windows. you'll want to convert it over to bash. judging from the content of the bat file above you should be able to do this with reasonable ease by checking out a few bash script tutorials online. it looks like all "echo this or that" and assigning variables.

---

### Post by Karlchen on 2011-04-18
Hello, Atul.

The posted Windows console script looks extremely similar to the script which you posted in another thread of yours only a few days ago: [**Running .bat file**]("http://ubuntuforums.org/showthread.php?t=1727851").
That script was meant to launch some Oracle sqlplus commands.
Today you try to run some MySQL server commands.

The two .bat files which you post(ed) look almost identical. In the other thread, your .bat script was translated to a bash .sh script.
I am a bit amazed that you ask the same question which has been answered before in this thread again.
Should you not be able to perform the translation from .bat to .sh for the second script yourself perhaps?

Kind regards,
Karl
--
P.S.:
MySQL related .bat file posted today: ```
@echo OFF
echo Welcome to the DB install and update utility for OneView.
set mySQLPath="C:\Program Files\MySQL\MySQL Server 5.0\bin\mysql.exe"
echo Default MySQL Path is %mySQLPath%. Please Edit bat file and change path if not correct.
set /P dbuser=Enter DB user name :
set /P dbpswd=Enter DB password  :
set /p dbname=Enter DB Name/SID  :

echo Connecting to the Database..
@echo off
SETLOCAL

echo deleting previous logs if any

del %temp%\OVMySQLDBInstall*.log
%mySQLPath%  -u%dbuser% -p%dbpswd%  %dbname% < 1.1\MySql\1.sql  2> %temp%\OVMySQLDBInstall1.log
%mySQLPath%  -u%dbuser% -p%dbpswd%  %dbname% < 1.3\MySql\1.sql  2> %temp%\OVMySQLDBInstall3.log
%mySQLPath%  -u%dbuser% -p%dbpswd%  %dbname% < 1.4\MySql\1.sql  2> %temp%\OVMySQLDBInstall4.log
%mySQLPath%  -u%dbuser% -p%dbpswd%  %dbname% < 1.5\MySql\1.sql  2> %temp%\OVMySQLDBInstall5.log
%mySQLPath%  -u%dbuser% -p%dbpswd%  %dbname% < 1.6\MySql\1.sql  2> %temp%\OVMySQLDBInstall6.log
%mySQLPath%  -u%dbuser% -p%dbpswd%  %dbname% < 1.7\MySql\1.sql  2> %temp%\OVMySQLDBInstall7.log
%mySQLPath%  -u%dbuser% -p%dbpswd%  %dbname% < 1.8\MySql\1.sql  2> %temp%\OVMySQLDBInstall8.log
%mySQLPath%  -u%dbuser% -p%dbpswd%  %dbname% < 1.9\MySql\1.sql  2> %temp%\OVMySQLDBInstall9.log

echo DB install and update utility for OneView has finished execution. 
echo merging log files

copy %temp%\OVMySQLDBInstall*.log %temp%\OVMySqlDBInstall.log
echo Log file for the session can be found at %temp%\OVMySqlDBInstall.log
pause     
```Oracle related .bat file posted in the other thread: ```
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
```Oracle related .bat file translated to .sh: ```
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
```

---

### Post by atulmittal_mds on 2011-04-18
Hello Karl,

I have tried this time to convert bat file into sh file from your previous file..but i got some errors...can u help me in pointing out the cause of error..

Converted file : 

#!/bin/bash
#
echo "Welcome to the DB install and update utility for OneView."
set mySQLPath="/etc/init.d/mysql"
echo Default MySQL Path is $mySQLPath. Please Edit bat file and change path if not correct.

echo "Enter DB user name : \c"
read dbuser
echo "Enter DB password : \c"
read dbpswd
echo "Enter DB Name/SID : \c"
read dbname

echo Connecting to the Database..

echo deleting previous logs if any
rm $TMP/OVMySQLDBInstall*.log
$mySQLPath  -u$dbuser -p$dbpswd  $dbname < 1.1/MySql/1.sql  2> $tmp%/OVMySQLDBInstall1.log
$mySQLPath  -u$dbuser -p$dbpswd  $dbname < 1.3/MySql/1.sql  2> $tmp%/OVMySQLDBInstall3.log
$mySQLPath  -u$dbuser -p$dbpswd  $dbname < 1.4/MySql/1.sql  2> $tmp%/OVMySQLDBInstall4.log
$mySQLPath  -u$dbuser -p$dbpswd  $dbname < 1.5/MySql/1.sql  2> $tmp%/OVMySQLDBInstall5.log
$mySQLPath  -u$dbuser -p$dbpswd  $dbname < 1.6/MySql/1.sql  2> $tmp%/OVMySQLDBInstall6.log
$mySQLPath  -u$dbuser -p$dbpswd  $dbname < 1.7/MySql/1.sql  2> $tmp%/OVMySQLDBInstall7.log
$mySQLPath  -u$dbuser -p$dbpswd  $dbname < 1.8/MySql/1.sql  2> $tmp%/OVMySQLDBInstall8.log
$mySQLPath  -u$dbuser -p$dbpswd  $dbname < 1.9/MySql/1.sql  2> $tmp%/OVMySQLDBInstall9.log

echo DB install and update utility for OneView has finished execution. 
echo merging log files

cat $tmp/OVMySQLDBInstall*.log > $tmp/OVMySqlDBInstall.log

echo Log file for the session can be found at $tmp/OVMySqlDBInstall.log
echo "Press the ANY key to continue \c"
read ANSW


When i tried to run this scripts it shows the following error:

Enter DB user name : atul
Enter DB password : atul
Enter DB Name/SID : test
Connecting to the Database..
deleting previous logs if any
rm: cannot remove `/OVMySQLDBInstall*.log': No such file or directory
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 18: cannot open 1.1/MySql/1.sql: No such file
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 18: -uatul: not found
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 19: cannot open 1.3/MySql/1.sql: No such file
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 19: -uatul: not found
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 20: cannot open 1.4/MySql/1.sql: No such file
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 20: -uatul: not found
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 21: cannot open 1.5/MySql/1.sql: No such file
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 21: -uatul: not found
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 22: cannot open 1.6/MySql/1.sql: No such file
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 22: -uatul: not found
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 23: cannot open 1.7/MySql/1.sql: No such file
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 23: -uatul: not found
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 24: cannot open 1.8/MySql/1.sql: No such file
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 24: -uatul: not found
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 25: cannot open 1.9/MySql/1.sql: No such file
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 25: -uatul: not found
DB install and update utility for OneView has finished execution.
merging log files
/home/atul/Atex1/branches/WSDB/DataBase/OVMySqlInstall.sh: 30: cannot create /OVMySqlDBInstall.log: Permission denied
Log file for the session can be found at /OVMySqlDBInstall.log


Thanks 
Best Regards,
Atul

---

### Post by Karlchen on 2011-04-18
Hello, Atul.

Hey, you see your translation from .bat script to .sh script is not half as bad as the error messages which you receive might suggest. In fact, it is almost perfect. :smile:

[U]Note, please:
[/U]On Windows, environment variables are enclosed by a pair of percent characters, e.g. %PATH%.
On Linux, environment variables are prefixed by a dollar sign, e.g. $PATH. In a few cases it is wise to add a pair of brackets to tell the shell where the variable name starts and where it ends, e.g. ${PATH}. In most cases, however, prefixing the dollar sign will be sufficient, giving $PATH.

You overlooked a few percent characters in the Windows .bat file and did not remove them. The Linux shell gets confused and does not find the folder. In particular, as the %TMP% variable on Linux is $TMP, not $tmp. Linux is case sensitive.

Here is a corrected version, hopefully I did not overlook anything. :)
Explanations have been added as comment lines. Comment lines in shell script start with a hash character (#).
```
#!/bin/bash
#
echo "Welcome to the DB install and update utility for OneView."

# set mySQLPath="/etc/init.d/mysql"
# set becomes export on Linux
# no double quotes required, because no blanks enclosed
# being familiar with Oracle, but not with MySQL, I am not sure
# whether you really have to launch /etc/init.d/mysql or some other
# executable
export mySQLPath=/etc/init.d/mysql

echo Default MySQL Path is $mySQLPath. Please Edit bat file and change path if not correct.

echo "Enter DB user name : \c"
read dbuser
echo "Enter DB password : \c"
read dbpswd
echo "Enter DB Name/SID : \c"
read dbname

echo Connecting to the Database..

echo deleting previous logs if any
# if you wish to avoid complaints about non-existing logfiles redirect the screen output
# rm $TMP/OVMySQLDBInstall*.log
rm $TMP/OVMySQLDBInstall*.log > /dev/null 2>&1

# In the next 7 commands the percent character must be removed after $tmp
# plus on Linux it is $TMP (uppercase, not lowercase)
$mySQLPath -u$dbuser -p$dbpswd $dbname < 1.1/MySql/1.sql 2> $TMP/OVMySQLDBInstall1.log
$mySQLPath -u$dbuser -p$dbpswd $dbname < 1.3/MySql/1.sql 2> $TMP/OVMySQLDBInstall3.log
$mySQLPath -u$dbuser -p$dbpswd $dbname < 1.4/MySql/1.sql 2> $TMP/OVMySQLDBInstall4.log
$mySQLPath -u$dbuser -p$dbpswd $dbname < 1.5/MySql/1.sql 2> $TMP/OVMySQLDBInstall5.log
$mySQLPath -u$dbuser -p$dbpswd $dbname < 1.6/MySql/1.sql 2> $TMP/OVMySQLDBInstall6.log
$mySQLPath -u$dbuser -p$dbpswd $dbname < 1.7/MySql/1.sql 2> $TMP/OVMySQLDBInstall7.log
$mySQLPath -u$dbuser -p$dbpswd $dbname < 1.8/MySql/1.sql 2> $TMP/OVMySQLDBInstall8.log
$mySQLPath -u$dbuser -p$dbpswd $dbname < 1.9/MySql/1.sql 2> $TMP/OVMySQLDBInstall9.log

echo DB install and update utility for OneView has finished execution.
echo merging log files

# $TMP, not $tmp
cat $TMP/OVMySQLDBInstall*.log > $TMP/OVMySqlDBInstall.log

echo Log file for the session can be found at $TMP/OVMySqlDBInstall.log
# any key won't do, "read" expects you to press enter
echo "Press the enter key to continue \c"
read ANSW
```HTH,
Karl

---

### Post by atulmittal_mds on 2011-04-19
Hello Karl,

Again i m very happy with your help.. the way u described is really appreciable.
Thanks once again Karl...be in touch..takecare

---

