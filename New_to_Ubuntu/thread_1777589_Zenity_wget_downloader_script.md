---
title: "Zenity wget downloader script"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-06-07
I like d4x but can not seem to find it in the new ubuntu 11.04 with apt-get install d4x I like d4x becuse it will let me control my download speed. So I got board and used zenity with wget and it still not perfect (I have poor programing skills). So fell free to use it if you need it. I just ask that you post the changes here so I can see what you did (learn from you the experts).

#!/bin/bash
wgeturl=$(zenity --entry --text="enter url");
zenity --info --text "Choose speed limit";
szlimitspeed=$(zenity --entry --text="1024 low 10240 med 0 unlimited");
zenity --info --text "Choose file save destination";
szSavePathto=$(zenity --file-selection --multiple --save --confirm-overwrite);
cd $szSavePathto
wget -c --limit-rate=$szlimitspeed $wgeturl | (if `zenity --progress --text="downloading" --percentage=1 --auto-close`;
                 then
                     echo 'download Job completed'
                 else
                     killall wget 
                     exit
                 fi)

---

