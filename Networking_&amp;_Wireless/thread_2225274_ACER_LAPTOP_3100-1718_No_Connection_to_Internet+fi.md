---
title: "ACER LAPTOP 3100-1718 No Connection to Internet+fix?"
date: 2014-05-20
forum: Networking &amp; Wireless
---

### Post by tomsubt on 2014-05-20
Hello Everyone, With my old verizon modem I connected to the internet right away after installing lubuntu 14.04
on my acer laptop, but I just got a new modem an Actiontec gateway GT784WN and it connected to the laptop ok but I cannot get it to connect to the internet for some reason. I have a wifi setup on my desktop and that connected to the internet right away with ubuntu.
Anyone know why I am not getting connected to the internet on the laptop. Please help if you can, any suggestions would be appreciated. Thank You

---

### Post by varunendra on 2014-05-21
On the laptop, please run "wireless_script" suggested in this post : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222) , and post back the report it generates.

---

### Post by tomsubt on 2014-05-21
ok I ran the script and here are the results from terminal>> tom@tom-Aspire-3100:~$ wget -N -t 5 -T 10 [https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script) && chmod +x wireless_script && ./wireless_script
--2014-05-21 10:16:16--  [https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 50.19.115.255
Connecting to dl.dropbox.com (dl.dropbox.com)|50.19.115.255|:443... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: [https://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script) [following]
--2014-05-21 10:16:16--  [https://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script)
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 54.225.207.37, 23.21.107.15, 107.22.177.184, ...
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|54.225.207.37|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15521 (15K) [text/plain]
Saving to: ‘wireless_script’

100%[======================================>] 15,521      --.-K/s   in 0s      

Last-modified header missing -- time-stamps turned off.
2014-05-21 10:16:17 (86.2 MB/s) - ‘wireless_script’ saved [15521/15521]



        **** PLEASE WAIT WHILE THE SCRIPT GENERATES THE REPORT ****
  
  If this takes more than 1 minute, you may abort the script by pressing
  "Ctrl+Z" on your keyboard.
  
  (Type your Login Password when asked, then press 'Enter')

[sudo] password for tom: 


    ########################################################################

    DONE! All results saved in -

		 File Name: 	"wireless-info.txt" 
		 Directory: 	"/home/tom"

    Please upload the above file or its contents where you are seeking help.

    ------------------------------------------------------------------------
    NOTE: Although we have taken full precaution to filter out all sensitive
          information, it is recommended to take a look at the file yourself
          to be double sure that it contains no sensitive data.
    ----------------------------------------------------------------

---

### Post by tomsubt on 2014-05-21
varunendra:   Solved, Thank You Very Much, that script did it, I am now on the internet(wifi)!!

---

### Post by varunendra on 2014-05-21
Actually the script only inspects the system, doesn't fix anything. It is purely a coincide that the wifi started working after running it. The script didn't do anything to fix it. :)

In case the problem reoccurs, please post back the report file that the script has generated in your Home directory -
> **tomsubt said:**
>     DONE! All results saved in -

		 File Name: 	"**[COLOR="#FF0000"]wireless-info.txt[/COLOR]**" 
		 Directory: 	"**[COLOR="#0000CD"]/home/tom[/COLOR]**"

    Please upload the above file or its contents where you are seeking help.

---

### Post by tomsubt on 2014-05-21
Ok, Will do, Thank You just glad it works now

---

