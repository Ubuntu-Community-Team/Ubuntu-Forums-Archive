---
title: "Dell  inspiron 1501"
date: 2015-02-06
forum: Networking &amp; Wireless
---

### Post by Vladimir1989 on 2015-02-06
Hi! I established ubuntu 14.10 on Dell  inspiron 1501, I have wire no connection Internet, only wi fi. But the network interface card doesn't work by default. And the computer doesn't define operation of the network interface card, and without it I can't download addition and the driver to start work with the computer. I from Russia, excuse for bad English). Somebody can help council? Thanks.

---

### Post by slickymaster on 2015-02-06
Hi Vladimir1989, welcome to the forums.

I moved your thread to the **Networking & Wireless** sub-forum, which is the proper venue for the type of problems you're facing.

Please download and run the [wireless script]("http://dl.dropboxusercontent.com/u/57264241/wireless_script"), which will diagnose the system. It can be ran by copying and pasting the command below in the terminal (ctrl+alt+t opens the terminal):```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
The command will download a script and create a file named (wireless-info.txt or wireless-info.txt.tar.gz) depending on the size of the file that you'll have to post back here in the thread.

---

### Post by Vladimir1989 on 2015-02-06
[[COLOR=#C61919]slickymaster[/COLOR]]("http://ubuntuforums.org/member.php?u=1753126")[COLOR=#000000] [/COLOR]Thanks!

Wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && CHMOD + &#1093; wireless_script && ./wireless_script
I have no connection with the Internet through ubuntu. Only windows 7 has wi fi on this computer.

---

### Post by slickymaster on 2015-02-06
> **Vladimir1989 said:**
> Wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && CHMOD + &#1093; wireless_script && ./wireless_script
I have no connection with the Internet through ubuntu. Only windows 7 has wi fi on this computer.
If you do not have ethernet connection then follow the [directions at this link]("http://ubuntuforums.org/showpost.php?p=12350385") for running the script without internet.

---

### Post by Hadaka on 2015-02-06
Hi, please copy and post the output of..
```
lspci -n |egrep '0200|0280' | awk '{print $3}'
rfkill list all | grep yes
lsmod | grep cfg80211
```
post the output
thanks.

---

### Post by chili555 on 2015-02-06
I have subscribed to the thread and will be very happy to help if needed. Hadaka and Slicky are very good, so I may not say a word!

---

### Post by Vladimir1989 on 2015-02-06
lspci -n |egrep '0200|0280' | awk '{print $3}'
rfkill list all | grep yes
lsmod | grep cfg80211

cfg80211              409394  2 b43,mac80211

[I][COLOR=#800000]To change this-
Open any folder > go to **Files > Preferences > Behavior tab > select "Ask each time"** option under "Executable Text Files" section.] [/COLOR][/I]I can't find preferences function))
**1) Right-click the downloaded file > click "Properties" > go to "Permissions" tab > tick the "Execute" checkbox > close the box. **It is made.

---

### Post by Hadaka on 2015-02-06
Hi, there were 3 lines of codes that i needed info on.
lspci -n |egrep '0200|0280' | awk '{print $3}'
rfkill list all | grep yes
lsmod | grep cfg80211[COLOR=#ff0000][/COLOR][COLOR=#ff0000]***[/COLOR]
cfg80211              409394  2 b43,mac80211[COLOR=#ff0000]***[/COLOR] you got this one...i still need to 2 others
Please copy and post one line at a time
```
lspci -n |egrep '0200|0280' | awk '{print $3}'
rfkill list all | grep yes
```
thanks

---

### Post by Vladimir1989 on 2015-02-06
&#1054;&#1082;.

[http://pastebin.ubuntu.com/10096293/](http://pastebin.ubuntu.com/10096293/)  Maybe it will be so more correct.

---

### Post by Hadaka on 2015-02-06
Hi, you are missing the firmware for your b43 driver,
go here..
[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)
post#7 - put it on a usb stick then on the ubuntu desktop
be sure to FIRST get the zip file then the commands
you do not need internet for this.

---

### Post by Vladimir1989 on 2015-02-06
[COLOR=#000000]Code:
lspci -n |egrep '0200|0280' | awk '{print $3}'
rfkill list all | grep yes[/COLOR]
14e4:4311
14e4:170c
[COLOR=#000000]

thanks[/COLOR]

mkdir: cannot create directory ‘/lib/firmware/b43’: File exists
-Inspiron-1501:~$ sudo cp Desktop/b43/* /lib/firmware/b43
cp: cannot stat ‘Desktop/b43/*’: No such file or directory
-Inspiron-1501:~$ sudo rmmod -f b43
-Inspiron-1501:~$ sudo rmmod -f ssb
rmmod: ERROR: ../libkmod/libkmod-module.c:769 kmod_module_remove_module() could not remove 'ssb': Resource temporarily unavailable
rmmod: ERROR: could not remove module ssb: Resource temporarily unavailable
-Inspiron-1501:~$ sudo modprobe b43
What not so?

---

### Post by Hadaka on 2015-02-06
ok..it says..
mkdir: cannot create directory ‘/lib/firmware/b43’: [COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR][COLOR=#ff0000]File exists[/COLOR]
so do.. 
```
sudo mv /lib/firmware/b43 /lib/firmware/b43/old
```

What not so?..so now make sure you have dropped the b43 zip file on the Desktop and try again.

---

### Post by Vladimir1989 on 2015-02-06
Probably I do something not so. I unpacked archive b43 in the folder on a desktop, then entered a code. But changed nothing.

sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

---

### Post by chili555 on 2015-02-06
> **Vladimir1989 said:**
> Probably I do something not so. I unpacked archive b43 in the folder on a desktop, then entered a code. But changed nothing.

sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43Just for testing purposes, reboot and then see if the wireless works. If not, check:```
sudo ls /lib/firmware/b43
```Do you see many firmware files in there like this?```
$ sudo ls /lib/firmware/b43
a0g0bsinitvals5.fw     lcn400initvals33.fw    sslpn1bsinitvals20.fw
a0g0bsinitvals9.fw     lp0bsinitvals13.fw     sslpn1bsinitvals27.fw
a0g0initvals5.fw       lp0bsinitvals14.fw     sslpn1initvals20.fw
a0g0initvals9.fw       lp0bsinitvals15.fw     sslpn1initvals27.fw
a0g1bsinitvals13.fw    lp0bsinitvals16.fw     sslpn2bsinitvals19.fw
a0g1bsinitvals5.fw     lp0initvals13.fw       sslpn2initvals19.fw
a0g1bsinitvals9.fw     lp0initvals14.fw       sslpn3bsinitvals21.fw
a0g1initvals13.fw      lp0initvals15.fw       sslpn3initvals21.fw
a0g1initvals5.fw       lp0initvals16.fw       sslpn4bsinitvals22.fw
a0g1initvals9.fw       lp1bsinitvals20.fw     sslpn4initvals22.fw
b0g0bsinitvals13.fw    lp1bsinitvals22.fw     ucode11.fw
etc., etc.
```If so, your wireless should be working. You needn't copy everything to post here; just tell us if they are there or not.

If not, one of us has missed a step and we'll have to retrace our steps.

---

### Post by Vladimir1989 on 2015-02-06
Code:sudo ls /lib/firmware/b43    There it is empty....   Once again I laid out all files from the folder 43 on a desktop and started sudo mkdir /lib/firmware/b43sudo cp Desktop/b43/* /lib/firmware/b43sudo rmmod -f b43sudo rmmod -f ssbsudo modprobe b43But changed nothing, when loading system there are some lines with b43 errors.

I will go to sleep, we have already three o'clock in the morning. But I will surely look as I will wake up that you will advise to do farther. Thanks.

---

### Post by jeremy31 on 2015-02-06
Let us see ```
ls ~/Desktop/b43
```

---

### Post by jeremy31 on 2015-02-06
> **Vladimir1989 said:**
> Code:sudo ls /lib/firmware/b43    There it is empty....   Once again I laid out all files from the folder 43 on a desktop and started sudo mkdir /lib/firmware/b43sudo cp Desktop/b43/* /lib/firmware/b43sudo rmmod -f b43sudo rmmod -f ssbsudo modprobe b43But changed nothing, when loading system there are some lines with b43 errors.

I bet that is the issue```
ls ~/Desktop | grep fw
``` and if you see all the files then

 ```
sudo cp ~/Desktop/*.fw /lib/firmware/b43/
```

---

### Post by Vladimir1989 on 2015-02-07
Hi, everybody!

-Inspiron-1501:~$ ls ~/Desktop/b43
 
ls ~/Desktop | grep fw
ls: cannot access /home/Desktop/b43: No such file or directory
-Inspiron-1501:~$ 
-Inspiron-1501:~$ ls ~/Desktop | grep fw
ls: cannot access /home/Desktop: No such file or directory
-Inspiron-1501:~$ sudo cp ~/Desktop/*.fw /lib/firmware/b43/
[sudo] password for: 
cp: cannot stat &#8216;/home/Desktop/*.fw&#8217;: No such file or directory
-Inspiron-1501:~$ 
I incorrectly inserted files on a desktop?

---

### Post by mörgæs on 2015-02-07
I know it's a little late to post this kind of advice, but anyway: 

If you had begun with bringing the computer to a place with wired internet access it might have been easier for you.

---

### Post by Vladimir1989 on 2015-02-07
Yes, you are absolutely right. I didn't assume that I will spend so much time for installation of one driver for ubuntu.

---

### Post by Hadaka on 2015-02-07
ok, let's see if i can clear some confusion..
please do..
Go to the ubuntu link i gave you with the b43=zip file ^WINDOWS 7^
Insert the mem stick.Drag and drop the b43=zip file to the USB mem stick ^Exit Windows ^
Boot up Ubuntu..drag and drop the b43-zip file from the USB to your Desktop.
Right click the b-43 icon on the Desktop chose extract here.
From your HOME directory
open a terminal ctrl/alt/t

and do..
```
sudo mkdir /lib/firmware/b43 #Creates Directory /lib/firmware/b43

sudo cp Desktop/b43/* /lib/firmware/b43 #Copies now extracted data FROM B43-ZIP to /lib/firmware/b43

sudo rmmod -f b43 #removes old b-43 module

sudo rmmod -f ssb # removes ssb module

sudo modprobe b43 #Inserts b43 module
```

---

### Post by Vladimir1989 on 2015-02-07
I loaded on usb the carrier the b43 file, passed to ubuntu, further extract here b43 on a desktop, further team 
sudo mkdir /lib/firmware/b43 #Creates Directory /lib/firmware/b43

sudo cp Desktop/b43/* /lib/firmware/b43 #Copies now extracted data FROM B43-ZIP to /lib/firmware/b43

sudo rmmod -f b43 #removes old b-43 module

sudo rmmod -f ssb # removes ssb module

sudo modprobe b43 #Inserts b43 module

And me in the terminal left

mkdir: cannot create directory &#8216;/lib/firmware/b43&#8217;: File exists
-Inspiron-1501:~$ sudo mkdir /lib/firmware/b43 #Creates Directory /lib/firmware/b43
mkdir: cannot create directory &#8216;/lib/firmware/b43&#8217;: File exists
-Inspiron-1501:~$ 
-Inspiron-1501:~$ sudo cp Desktop/b43/* /lib/firmware/b43 #Copies now extracted data FROM B43-ZIP to /lib/firmware/b43
cp: cannot stat &#8216;Desktop/b43/*&#8217;: No such file or directory
-Inspiron-1501:~$ 
-Inspiron-1501:~$ sudo rmmod -f b43 #removes old b-43 module
rmmod: ERROR: ../libkmod/libkmod-module.c:769 kmod_module_remove_module() could not remove 'b43': No such file or directory
rmmod: ERROR: could not remove module b43: No such file or directory
-Inspiron-1501:~$ 
-Inspiron-1501:~$ sudo rmmod -f ssb # removes ssb module
rmmod: ERROR: ../libkmod/libkmod-module.c:769 kmod_module_remove_module() could not remove 'ssb': Device or resource busy
rmmod: ERROR: could not remove module ssb: Device or resource busy
-Inspiron-1501:~$ 
-Inspiron-1501:~$ sudo modprobe b43 #Inserts b43 module


I don't understand this operating system. What again not so?

---

### Post by chili555 on 2015-02-07
[ATTACH=CONFIG]259790[/ATTACH]

Let's take this step by step. Did you download the file b43.zip to your desktop as was posted above? Do you see it there?

---

### Post by chili555 on 2015-02-07
Did you right-click it and select 'Extract Here'?

[ATTACH=CONFIG]259791[/ATTACH]

---

### Post by chili555 on 2015-02-07
After you extracted the b43.zip file, did you get a folder named 'b43'?

[ATTACH=CONFIG]259794[/ATTACH]

---

### Post by chili555 on 2015-02-07
Now we can copy all the firmware files from the folder on your desktop to the correct folder in /lib/firmware:```
sudo mkdir  /lib/firmware/b43
```If the file exists, that's fine, just continue:```
sudo  cp  ~/Desktop/b43*  /lib/firmware/b43
```Now we unload the driver module and reload it so the driver sees the nice, new firmware:```
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe b43
```Your wireless should now be working.

---

### Post by Vladimir1989 on 2015-02-07
I made everything as is written above and began reset, but ubuntu didn't answer more than 10 minutes on reset, and I forcibly switched off the computer. At restart of ubuntu the system indicates mistakes in the driver. I made two screenshots, but windows 7 doesn't give access to these pictures.

-Inspiron-1501:~$ sudo mkdir  /lib/firmware/b43
[sudo] password for: 
mkdir: cannot create directory ‘/lib/firmware/b43’: File exists
-Inspiron-1501:~$ sudo  cp  ~/Desktop/b43*  /lib/firmware/b43
cp: cannot stat ‘/home/Desktop/b43*’: No such file or directory
-Inspiron-1501:~$ sudo modprobe -r b43
-Inspiron-1501:~$ sudo modprobe -r ssb
modprobe: FATAL: Module ssb is in use.
-Inspiron-1501:~$ sudo modprobe b43

---

### Post by jeremy31 on 2015-02-07
Lets see where one of the files are ```
locate ucode5.fw
```

---

### Post by chili555 on 2015-02-07
Is 'Desktop' called something else in the Russian version of Ubuntu? May we see:```
cd ~
ls
```Also, I think you have the command incorrectly typed. You said:> sudo cp ~/Desktop/b43* /lib/firmware/b43But I asked for:> sudo cp ~/Desktop/b43[COLOR="#FF0000"]/[/COLOR]* /lib/firmware/b43It is important that the commands be exactly correct.

---

### Post by Vladimir1989 on 2015-02-07
[COLOR=#000000]Code:[/COLOR]
locate ucode5.fw

I didn't understand this team, after it there has to be a text document with results? In a screenshot it is.

Also, I think you have the command incorrectly typed. You said:[I]sudo cp ~/Desktop/b43* /lib/firmware/b43
[/I]

I simply copy all teams and I insert from here, without the amendments and changes. I apply a screenshot.

Yes, still. Ubuntu at switching off or reset is very long loaded, I can't wait so much, penultimate time I expected more than 10 minutes and simply switched off the computer.

---

### Post by jeremy31 on 2015-02-07
This option should work ```
sudo apt-get install nautilus-open-terminal
``` Reboot, then right click on the desktop and choose 'open in terminal' then in terminal```
sudo cp /b43/* /lib/firmware/b43/
``` and reboot again if it has no errors

---

### Post by chili555 on 2015-02-07
According to your screenshot, you have no directory called 'Desktop.' I suspect it is &#1088;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;. Please change the command to:```
sudo cp ~/&#1088;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;/b43/*  /lib/firmware/b43
```At least in English, Ubuntu doesn't like names with a space in the middle. You may have to tell Ubuntu to escape the space with:```
/sudo cp ~/&#1088;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081;[COLOR="#FF0000"]\ [/COLOR]&#1089;&#1090;&#1086;&#1083;/b43/*  /lib/firmware/b43
```If it seems to work as expected with no error, simply reboot.

---

### Post by Vladimir1989 on 2015-02-07
So far it is ineffectual.

---

### Post by chili555 on 2015-02-07
Can you change directories to the desktop?```
cd ~/&#1088;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081;\ &#1089;&#1090;&#1086;&#1083;/
```And then list its contents to see if the folder b43 is there?```
ls
```We are very sorry that we don't really understand or write the Russian language. You must surely know what 'desktop' is called in your Ubuntu system. Please help us a bit here!

---

### Post by Vladimir1989 on 2015-02-07
In Russian desktop it - &#1088;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;. When loading there is a message of checking disk drivers for error. It is time for me to sleep, let's continue tomorrow.

---

### Post by Hadaka on 2015-02-07
Please try one of these,,,one line at a time...

$ CD &#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; \ &#1089;&#1090;&#1086;&#1083;   
$ CD «&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;» 
  $ CD '&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;'

---

### Post by Vladimir1989 on 2015-02-08
On the second screenshot it is visible that my desktop is called as ubuntu desktop.

---

### Post by Hadaka on 2015-02-08
ok, that was "uppercase" CD , show me
with lowercase cd

  cd &#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; \ &#1089;&#1090;&#1086;&#1083;   
  cd «&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;» 
  cd    '&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;'

thank you

---

### Post by Vladimir1989 on 2015-02-08
So that's that.

---

### Post by chili555 on 2015-02-08
Now, please list the contents of the directory:```
ls
```Is the folder b43 shown? If so, now copy the firmware files:```
sudo cp b43/*  /lib/firmware/b43
```If there are no errors, reboot.

---

### Post by Vladimir1989 on 2015-02-08
Without changes.

---

### Post by chili555 on 2015-02-08
In your previous screenshot, you had changed directories to &#1088;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;. In this screenshot, you are not. Please try again.

---

### Post by Vladimir1989 on 2015-02-08
Not absolutely I understand about what you speak, in the previous screenshot there were these commands [COLOR=#000000]cd &#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; \ &#1089;&#1090;&#1086;&#1083; [/COLOR]
[COLOR=#000000]cd «&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;» [/COLOR]
[COLOR=#000000]cd '&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;'[/COLOR]

---

### Post by chili555 on 2015-02-08
[ATTACH=CONFIG]259831[/ATTACH]

Please see your screenshot 98.jpg at post #45. I think you did:```
cd '&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;'
```Then you were in the directory containing the folder b43. 

Now in your most recent screenshot, you are in the directory ~. Please try again:```
cd '&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;'
```Now list the contents of the directory:```
ls
```Do you see the folder b43? If so:```
sudo cp b43/*  /lib/firmware/b43
```Reboot.

---

### Post by Vladimir1989 on 2015-02-08
Thanks for details, now I will try.

Computer freezes in case of reset. In case of new switching on there was a text of checking disk drives for errors.

---

### Post by Hadaka on 2015-02-08
Hi, you have an extra space in your command
please correct and try again..

```
sudo cp Desktop/b43/* /lib/firmware/b43  #correct 1 space
sudo cp Desktop/b43/*[COLOR=#ff0000]^^[/COLOR]/lib/firmware/b43 #not correct 2 spaces
```

---

### Post by mörgæs on 2015-02-08
In stead of posting screen shots please copy the relevant text and post in CODE tags.

---

### Post by Vladimir1989 on 2015-02-08
-Inspiron-1501:~$ cd '&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;'
-Inspiron-1501:~/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;$ ls
b43
-Inspiron-1501:~/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;$ sudo cp Desktop/b43/* /lib/firmware/b43
[sudo] password for :
cp: cannot stat &#8216;Desktop/b43/*&#8217;: No such file or directory
-Inspiron-1501:~/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;$ 
Without changes.

---

### Post by Hadaka on 2015-02-08
please enter this command,,
```
sudo cp b43/* /lib/firmware/b43
```
if it runs correctly, you will not get a return message.
let me know what happens
thanks.

---

### Post by chili555 on 2015-02-08
It ran correctly the first time. Please reboot.

---

### Post by Vladimir1989 on 2015-02-08
-Inspiron-1501:~$ sudo cp b43/* /lib/firmware/b43
[sudo] password for: 
cp: cannot stat &#8216;b43/*&#8217;: No such file or directory
-Inspiron-1501:~$ sudo cp b43/* /lib/firmware/b43
cp: cannot stat &#8216;b43/*&#8217;: No such file or directory
-Inspiron-1501:~$ 

I included reset, passed more than 10 minutes, but the computer doesn't respond. It was necessary to switch off manually.

---

### Post by Hadaka on 2015-02-08
whydo you keep changing the directory?
for this to work..you need to follow direction
change the directory back to       -Inspiron-1501:~/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;
so at the -Inspiron-1501:~/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083; prompt
please do 
```
sudo cp b43/* /lib/firmware/b43
```
thanks.

---

### Post by Vladimir1989 on 2015-02-08
-Inspiron-1501:~$ /&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;
bash: /&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081;: No such file or directory
natasha@natasha-Inspiron-1501:~$ ~/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;
bash: /home/natasha/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081;: No such file or directory
-Inspiron-1501:~$ ~/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083; prompt
bash: /home/natasha/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081;: No such file or directory
-Inspiron-1501:~$ /&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083; prompt
bash: /&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081;: No such file or directory
-Inspiron-1501:~$

---

### Post by chili555 on 2015-02-08
You must tell the terminal to change directories: cd. 

Please try:```
cd '&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;'
```Now list the contents of the directory:```
ls
```Do you see the folder **[COLOR="#0000CD"]b43[/COLOR]** in there? If so, please do:```
sudo cp b43/*  /lib/firmware/b43
```And then reboot.

---

### Post by Vladimir1989 on 2015-02-08
-Inspiron-1501:~$ cd '&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;'
-Inspiron-1501:~/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;$ ls
b43
-Inspiron-1501:~/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;$ sudo cp b43/*  /lib/firmware/b43
[sudo] password for : 
-Inspiron-1501:~/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;$ 

After that I click to reboot, and passes more than 10 minutes, but ubuntu doesn't respond and I switch off the computer manually. Between times I thank all who helps to understand a problem, for their councils and attention. It's time to go to bed. In Russia two o'clock in the morning. Thanks.

---

### Post by chili555 on 2015-02-08
I am suspicious that you have another problem aside from wireless. We have tried our best to help you and overcome the language barrier. I believe you can get help here from experts who understand you and whom you understand. Please ask your further questions here: [http://forum.ubuntu.ru/](http://forum.ubuntu.ru/)

I regret we can be of no more assistance.

---

### Post by mörgæs on 2015-02-09
If you want to begin again I recommend installing Lubuntu. Most people will find Ubuntu too heavy for this computer.

Just bring it to a place where you get wired internet access.

---

### Post by Vladimir1989 on 2015-02-09
Thanks. At this forum I already created a separate branch before, there nobody answered. But it isn't terrible. I will postpone
 acquaintance to ubuntu till more suitable times.

---

### Post by Vladimir1989 on 2015-02-09
[http://forum.ubuntu.ru/index.php?topic=257108.0](http://forum.ubuntu.ru/index.php?topic=257108.0)

---

### Post by mörgæs on 2015-02-09
You would help the people reading the Russian thread if you linked back to this one.

---

### Post by Vladimir1989 on 2015-06-06
[FONT=Arial]Hi all[/FONT][FONT=Arial]. [/FONT][FONT=Arial]For those who [/FONT][FONT=Arial]encounter [/FONT][FONT=Arial]a similar problem [/FONT][FONT=Arial]on this model [/FONT][FONT=Arial]of laptop I [/FONT][FONT=Arial]tell you [/FONT][FONT=Arial]a simple [/FONT][FONT=Arial]solution which [/FONT][FONT=Arial]worked [/FONT][FONT=Arial]for me personally[/FONT][FONT=Arial]:

Code[/FONT][FONT=Arial]:[/FONT]
[FONT=Arial]sudo apt[/FONT][FONT=Arial]-get purge [/FONT][FONT=Arial]bcmwl[/FONT][FONT=Arial]-[/FONT][FONT=Arial]kernel-source[/FONT][FONT=Arial] 

[/FONT][FONT=Arial]And reboot[/FONT][FONT=Arial]. [/FONT][FONT=Arial]Wi[/FONT][FONT=Arial]-fi [/FONT][FONT=Arial]works for me [/FONT][FONT=Arial]without problems. 

[http://ubuntuforums.org/showthread.php?t=2277779&highlight=dell+inspiron+1501](http://ubuntuforums.org/showthread.php?t=2277779&highlight=dell+inspiron+1501)

[/FONT]

---

