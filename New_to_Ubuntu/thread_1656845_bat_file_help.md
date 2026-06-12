---
title: "bat file help"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by billy192 on 2010-12-31
Hi,
as you will guess i am new to this Ubuntu stuff. 
I have a windows box that controls my CCTV cameras. They FTP a JPEG (motion dection) to the c:drive into their own folder.
  I have a bat file that runs in scheduler that creates a folder on an external HD for each camera with that days date as the folder name then deletes the files on the C drive. Then I have a second bat file that runs at the end of the month that creates a folder with the that months date and copies all the days folders in to it.
   
  My question if I put the code on here can someone help converting to run on Ubuntu?
  I have a  1 U sever running VM EXSi. I would like to ditch the windows server.
  Many Thanks
  Niel


:confused:

---

### Post by blind2314 on 2010-12-31
I'm not sure if this is what you want, but try these. The first snippet is a daily script, the second is monthly. You can schedule them with cron, I can help with that as well. If you dont think is close enough, post your code, and I can revise mine..maybe?

#!/bin/bash

DATE=`date +%F`
cd /home/xxx/
if [ -d $DATE ]; then

    mkdir "$DATE"
else
    echo "Directory already exists"
fi

cp -p /home/xxx/* $DATE
rm /home/xxx/*



#!/bin/bash

DATE=`date +%F`
MONTH=`echo $DATE | cut -d "-" -f1,2`
cd /home/xxx/

if [ -d $MONTH ]; then

        mkdir $MONTH
else
        echo "Directory already exists"
fi

cp -rp /home/xxx/* $MONTH

---

### Post by billy192 on 2010-12-31
thanks _[blind2314]("http://ubuntuforums.org/member.php?u=1214840")_


**_day_**

@echo off
:: variables
set drive= C:\garage
set folder=%date:~0,2%-%date:~3,2%-%date:~6,4%
set backupcmd=xcopy /c /h /i /r /k /y 

echo ######## PLEASE WAIT FOR BACKUP########...
echo %folder%
%backupcmd% "C:\garage\*.jpg" "f:\DAYS\garage\%folder%\"
del "C:\garage\*.jpg"

echo !!!!!!!!BACKUP COMPLETED  billy!!!!!!!!



**_month_**

@echo off
:: variables
set drive= F:\CAMREAMONTH

set yyyy=%date:~6,4%
set mm=%date:~3,2%
:: Subtract a month
set /A mm=%mm% - 1
:: Ahhh! but if month is already 1 then change to 12
:: ... and subtract one from the year! (i.e Jan 2009 minus 1 is Dec 2008
if "%mm%"=="0" set /A mm=12
if "%mm%"=="12" set /A yyyy=%yyyy% - 1

set folder=%mm%-%yyyy%

set backupcmd=xcopy /c /h /i /r /E /k /y 



echo ######## PLEASE WAIT FOR BACKUP########...
echo %folder%
%backupcmd% "F:\DAYS" "F:\CAMERAMONTH\%folder%\"


RMDIR F:\DAYS /S /Q




MD F:\DAYS\Tank
MD F:\DAYS\back
MD F:\DAYS\frontlh
MD F:\DAYS\frontrh
MD F:\DAYS\Garage

---

