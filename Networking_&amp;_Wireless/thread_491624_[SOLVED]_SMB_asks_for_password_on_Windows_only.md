---
title: "[SOLVED] SMB asks for password on Windows only"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by victorbrca on 2007-07-03
Hi all,


  I've configured SMB daemon on one of my Ubuntu servers at home. I can access the share from any Linux computer, but it asks for my password if I try to access from a Windows PC. Worse, it doesn't even accept any user password. 

  Would anyone mind shinning some light on me???  :)


Thanks,


Vic.

---

### Post by victorbrca on 2007-07-03
Solved this by adding the following string to the config file:

```
[Share name]
writable = yes
path = /path/to/directory
public = yes
guest ok = yes
guest only = yes
guest account = nobody
browsable = yes
```

And modifying lines:

```
security = share
```

and

```
guest account = nobody
```



Vic.

---

### Post by Mad_Max_1412 on 2007-07-03
Guys,

I am wondering whether this will fix my problem as well as it sounds similar.  I'm a newbie to Ubuntu, but had an old computer and wanted to trial Ubuntu with it as well as install a large hard drive to use as a repository for some media files.

These media files are to be accessed by my Zensonic media player which currently connects to my 2 Windows machines (Lounge and Office) fine.

I've created a directory called "Ubuntu_Videos" and installed SMB and also set up the workgroup to be the same as my Office and Lounge PC's. When I go to the Zensonic MP, and select "SMB directory" it still only shows "Office" and "Lounge" as being available to select from.  (I called my Ubuntu box "Ubuntu" during the install - not very original I know).

If I go to my Windows computer and click on Network Places, and then my workgroup name, I see all 3 computers.  Clicking on either Lounge or Office immediately show all my shared folders, but when I click on Ubuntu, it prompts for a username and password and then shows my shared folders such as "Ubuntu_Videos".  Would this "requesting" of username and password be the reason the Zensonic MP can't see Ubuntu at the moment and if so, would the above advice fix this?  I just want to confirm this before I start modifying files willy-nilly since I'm a newbie and don't want to stuff things up too much.

Cheers
Max

---

### Post by Andra on 2007-07-04
What is Zensonic media player? What operating system, what graphical or other interface does it use?

---

### Post by Mad_Max_1412 on 2007-07-04
Hi,

The best thing would be for me to point you to the website as it would have all the details:

[http://www.z500series.com/](http://www.z500series.com/)

Basically I turn it on and there are a couple of menus: Music, Video, Pictures, Settings, Extras

Extras takes you to a screen which uses the internet connection via the network to show you the weather report for your city.

Settings takes you to a screen which has sub menus for setting IP address, workgroup name etc.

Music, Video and Pictures takes you to a screen where you have a menu of how to access these types.  From memory they are: USB device, SMB devices, CD-ROM

I select SMB devices and the next screen shows which computers it can see, which in my case are the 2 windows computers called "Lounge" and "Office".  When I select one of them, it then shows the shared directories on that machine and when I select the directory, I see the files.  I select the file and it plays the video, music or shows the picture.

As I mentioned earlier, when I go to my Windows machine and go to "My Network Places" and click on my workgroup, it shows all 3 computers: "Lounge", "Office" and "Ubuntu".

Clicking on "Lounge" or "Office" immediately shows the shared directories, whereas clicking on "Ubuntu" prompts me for a username and password before it shows the shared directory.

That's why the previous post looks like it might be something I need to set up.  One question I meant to ask was where is this config file that Victorbrca talks about?

Thanks

---

### Post by wjp.reg on 2007-07-04
> One question I meant to ask was where is this config file that Victorbrca talks about?


You can find it here ```
/etc/samba/smb.conf
```

It's a good idea to make a backup of the file first like:

```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.original
```

and then make your changes:

```
gksudo gedit /etc/samba/smb.conf
```

and then test your changes with 

```
testparm /etc/samba/smb.conf
```

and then restart samba with

```
/etc/init.d/samba restart
```

good luck!

---

### Post by #Reistlehr- on 2007-07-04
doo..

```
adduser username
```
then do
```
smbpassword -a username
```

enter passwords when required.

i ran into this problem too

you cant add a user to samba if it does NOT exist locally already. so, add it to the system, then samba and you're set!

hopefully that helps some.

---

### Post by Mad_Max_1412 on 2007-07-06
Hi Guys,

I've got the Zensonic Media Player to see the Ubuntu computer, and I think setting a static IP address and the domain helped with this.

As for seeing my Ubuntu_Vids folder, I can see it in Windows Explorer but I can't copy any files across to it.  I also set my root directory (/home/max) as visible but I really only need to see the "Ubuntu_Vids" directory - /home/max/Ubuntu_vids

I've attached my smb.conf file so you can see where I might have gone wrong.  In Windows, if I right click on the Ubuntu_Vids folder and look at the properties, it shows as being Read-only.

I gather I should just delete the section for /home/max so I don't see that in my shared directories since I don't need it (so I've put # in there at the momet), but I'm not sure where I'm going wrong in not being able to transfer files to the Ubuntu_Vids directory.

Any assistance would be appreciated.

Ps I've renamed the file with a txt extension so I could upload it.


Max

---

### Post by Mad_Max_1412 on 2007-07-06
Guys,

I fixed it but it wasn't through using the smb.conf file.

I went to "Places" pull down menu, selected "Home Folder" and then I right-clicked on "Ubuntu_Vids", select properties, went to permissions tab and set the folder access for  Owner (Max), Group (Max) and Others to "Create and Delete Files".

I then went back to my Windows machine and i was able to copy a file from my windows machine to the Ubuntu_Vids folder.

Is this just a case of another way to achieve what I want, or was this wrong and I should be doing it via settings in the smb.conf file??

Thanks

MAx

---

### Post by victorbrca on 2007-07-06
It has nothing to do with the smb.conf, but with one the main security features of Linux, file and folder permissions.

  You can do the same from command line by using chmod and chown commands. They are extremely useful tools. 

  To find out who have access to your files, go to the folder on shell and type "ls -l". You will see something like this:

```
drwxr-xr-x 5 internals internals 4096 2007-06-05 13:18 .
drwxr-xr-x 6 root      root      4096 2007-06-02 16:38 ..
drwxr-xr-x 2 internals internals 4096 2007-05-23 18:46 backup
-rw------- 1 internals internals 8555 2007-07-03 16:58 .bash_history
-rw-r--r-- 1 internals internals  220 2007-05-21 15:18 .bash_logout
-rw-r--r-- 1 internals internals  414 2007-05-21 15:18 .bash_profile
-rw-r--r-- 1 internals internals 2227 2007-05-21 15:18 .bashrc
drwxr-xr-x 3 internals internals 4096 2007-06-01 10:45 downloads
-rw------- 1 internals internals   35 2007-07-06 04:25 .lesshst
-rw------- 1 internals internals 1109 2007-06-01 10:43 .mysql_history
-rw------- 1 root      root       188 2007-07-03 16:57 .nano_history
drwx------ 2 internals internals 4096 2007-05-23 08:57 .ssh
```

  The first few characters tell you who have access and what access they have.

  [_More info_]("http://catcode.com/teachmod/index.html")



Vic.

---

### Post by Mad_Max_1412 on 2007-07-06
Thanks for all your help.

Appreciated.

---

### Post by patrick295767 on 2007-07-09
> **victorbrca said:**
> Hi all,


  I've configured SMB daemon on one of my Ubuntu servers at home. I can access the share from any Linux computer, but it asks for my password if I try to access from a Windows PC. Worse, it doesn't even accept any user password. 

  Would anyone mind shinning some light on me???  :)


Thanks,


Vic.

Sharing folders for windows via your linux debian server    [http://patrick295767.pa.funpic.org/debian/howtos.htm](http://patrick295767.pa.funpic.org/debian/howtos.htm)

---

### Post by Mad_Max_1412 on 2007-11-17
Guys,

As you can see from my entries above, I originally did have some problems with SMB sharing with my Zensonic Media Player, but everything had been working flawlessly since early July.

Just to recap, I have a TV card on my Windows machine, and I tape various TV shows, trim them up and then transfer them via Windows Explorer to my Ubuntu directory called "Ubuntu_Vids" via a mapped drive within Windows Explorer.

Then I access these videos on my Zensonic Media Player which simply looks for SMB shares on the network.

Anyway, today I started up the Zensonic MP and within it's menu, I navigated (as usual) to Videos --> Ubuntu --> Ubuntu_Vids but when I select the Ubuntu_Vids directory (or another SMB shared directory I have on my Ubuntu box), I just get the hourglass waiting icon rather than a listing of the files.  When I select videos, it shows a list of computers on the network and then I select Ubuntu and the 2 shared directories (Ubuntu_Vids and another one called "Backup") appear immediately, but it's when I select either of these directories that it won't show the file listings.

Out of the 2 components (the Zensonic MP and the Ubuntu computer), only the Ubuntu computer has had changes due to the Update manager.  The Zensonic MP has not had any configuration changes or firmware changes.

One thing to note is that the /etc/samba/smb.conf file currently has a date/time stamp of  Sat 17 Nov 2007 9:42am which is roughly when I allowed the Update Manager to install about 28Mb of updates that it told me were available.

I've copied the smb.conf file as smb.txt so I could upload it if you want to examine it.  Even though it's got a recent date/time stamp, I can't see what's wrong with the last section (or what's been changed) in regards to the Ubuntu_Vids and Backup sections.

Currently I am having to go to my Windows machine and using the mapped drive via Windows Explorer, copy any video I have in the Ubuntu_Vids directory on my Ubuntu machine back into a shared folder on my Windows machine so I can access it with my Zensonic Media Player.

Any ideas would be greatly appreciated.

BTW, in case you are wondering why I just don't leave my video files on the Windows machine, here's the reasons:

1. Trying to learn about Ubuntu so I'm still using Windows whilst learning Ubuntu.

2.  Built the Ubuntu box with a very large drive as I wanted to use it as a Network Storage Device (NAS) and up to this morning it was working great.

3. My Windows machine doesn't have a lot of spare hard drive room and what it does have is needed for recording of the TV shows.  I don't want to waste money buying a second hard drive when I've got plenty of room on the Ubuntu box for storage.

Thanks again.
 

**** EDITED 30 Minutes After Posting ****

Guys,

Forget about it.  After posting my question and doing some other work, I thought I would just kick off the Update Manager even though there was no notification icon in the taskbar.  Lo and behold, there were 4 important security updates, all relating to SAMBA, of about 11.9MB.  The first one was "libsmbclient" which was a shared library that allows applications to talk to SMB/CIFS servers.

After doing the updates, my smb.conf file's date/time stamp was updated to the current time.  I then went and started my Zensonic MP and it accessed the Ubuntu_Vids directory fine, showing all my video files.

Problem solved. It looks like a rogue update from this morning, as I do recall seeing some SMB updates at that time.

Cheers

---

