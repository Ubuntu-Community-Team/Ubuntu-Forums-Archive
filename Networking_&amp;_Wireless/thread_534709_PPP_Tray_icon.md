---
title: "PPP Tray icon"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by gborzi on 2007-08-25
I have made a little python-gtk tray icon that works as an interface to pon/poff commands and monitors the presence of ppp connections. I needed such an application but was unable to find one. The closest one available in the repositories is gpppon but it's ugly, doesn't monitor the connection and takes too much space on the desktop.
So I decided to write this application by myself, looked for the easiest way to do it and decided to use python-gtk. I had not previous knowledge of python and its gtk extension, but being a programmer (Fortran - C - C++) it was quite easy to learn enough in a short period of time. Obviously, an expert python programmer can write this application much better.
Please let me know if you find this application useful, and report any bug on this thread.

The application is very small, so I attach the package and the tar.gz file below, along with some screenshots (menu while connected, menu while unconnected, configuration dialog).

EDIT: I have made a little change to the code to deal with the (rare) case when an user takes out all connections from the menu.

---

### Post by Nekiruhs on 2007-08-25
Just curious, I have been dying to figure out how to take Python programs and make Debs out of them. How did you do it?

---

### Post by gborzi on 2007-08-25
I downloaded the sources for driconf and plagiarized its "debianization".

---

### Post by hermes25 on 2007-08-25
This is great, i've been looking for something like this for some time!

---

### Post by migatxu on 2007-08-25
Yeah! Little and simply, and efficient! Good work guy! :guitar: I love you! : D

Edit: Just edit for thread subscription

---

### Post by gborzi on 2007-08-26
Thanks guys for your appreciation. I realized that I have made the post in the wrong subforum. Do you have any suggestion on where should I re-post ?

---

### Post by gborzi on 2007-08-27
I corrected some bugs in the configuration and the package. Please download this latest version, it's attached to the first post.

---

### Post by migatxu on 2007-08-27
Ok thanks :)

---

### Post by Marktrix on 2007-08-28
Thanks a lot :KS

---

### Post by gbentley321 on 2007-08-28
Thank you for this wonderful little app. I just took gnome-ppp and wvdial off my xfce desktop.
   Is there an easy way to show the connection speed in the mouseover? With dialup, I   
   sometimes have to try 2 or 3 times to get a fast enough connection.  
  Makes me want to learn Python.:)
   
  Thanks again,
  gbentley321

---

### Post by gborzi on 2007-08-28
I think it should be quite easy to add the connection speed, using pppstats. The only problem is that it can make the application more resource-ungry. I'll try to do it.
BTW, another thing I think could be useful, is the ability to execute a command (for example, playing a sound) after a given amount of time and/or at regular intervals or when the amount of received bytes reaches a user-specified threshold.

---

### Post by gborzi on 2007-08-28
Hello gbentley321,
I have made a modification to the code in order to display the time, speed and data in the tooltip. I'm attaching a screenshot and a modified ppptrayicon.py . gunzip the file and as root copy it over the previous file. If you have used the .deb the file to change is in /usr/lib/python2.5/site-packages/ppptrayicon.py . I would like to make some improvements to the configuration dialog before releasing another version and the associated package.

---

### Post by gbentley321 on 2007-08-29
Wow!, thats fast...
Thanks, I'll try it tonight.
gbentley321:)

---

### Post by gbentley321 on 2007-08-30
gborzi,
        It's working just fine, and I uninstalled the network monitor plugin
   (which does not work correctly anyway), so resource-wise, I probably
   am still better off than with gnome-ppp.
       When I said "connection speed" earlier, I guess I should have said
    "the speed at which I connected", as in "Connected at 28 KBs". Sometimes
    I connect at 14400 or even 9600 and I have to redial for a faster connect.
    I hope you keep working on this. I'm sure it will be real popular with the
    lightweight desktop folks. My openbox machine already has a copy on it.
    More thanks,
    gbentley321

---

### Post by mekgp on 2007-08-30
Very good application! Thanks!:KS

---

### Post by antmenj on 2007-08-30
Cool this type of thing should be included with the next release.  I wish we had had this a year or so back.  Keep it simple and small.:)

56.9% of internet users round here are on dialup so its worth it I say.

To bad I now have a smoothwall box:-s

---

### Post by gborzi on 2007-08-30
Thanks for your appreciation guys! The application is currently listed at [http://www.getdeb.net](http://www.getdeb.net) and [http://www.gnomefiles.org](http://www.gnomefiles.org) .

@gbentley321
How do you look at the connection speed, I mean is there a command that gives such data or do you have to look in the log files? I've checked pppstats and pppstatus manpages, without finding anything. If it's in the log files, please send me a snippet of them where there is this data, I don't have a dialup connection (only ADSL through USB and GPRS).

@antmenj
If the application will be successful, I'll propose it to REVU. BTW, it can be used with any connection that can be activated with a pon <something>, so with dialup, GPRS and USB-ADSL.

Regards.

---

### Post by Crinos512 on 2007-09-12
[COLOR="Blue"]**RE: Connection Speed.[/COLOR]** 
That information is indeed in the Log file.
Here is a Macro$haft article on the subject. [http://support.microsoft.com/kb/227695]("http://support.microsoft.com/kb/227695") the info should be valid though as the log is just a record of the hardware's communication.

[COLOR="#0000ff"]**My Question:**[/COLOR] I currently use GnomePPP to dial out. What do I need to do to be able to connect and disconnect using this icon? ...Also, please tell me this is not going to automaticlly connect me when I log in to Ubuntu. ( I hate that. :mad:)

---

### Post by gborzi on 2007-09-12
Hello Crinos512,
thanks for your help, but I had already seen, through a google search, that the connection speed is in the log files. The problem is that it is not always logged, it depends on the pppd loglevel. So, I won't implement it because it could work only on some installations. An alternative would be to add the output of a command to the tooltip, so that if someone needs that information he/she can:
1) change the loglevel;
2) add a *grep "Connected at" /var/log/messages |tail -n 1|gawk ...* command;
3) hope for the best.
As for your question: this program is an interface to pon/poff, so you need to configure your connections in such a way they will work with pon/poff. And no, it won't connect you at login, only when you ask for it.

Regards.

---

### Post by gborzi on 2007-10-28
Hello to everyone,
I have just released version 0.2 of PPP Tray Icon. It is available at [getdeb]("http://www.getdeb.net/search.php?keywords=ppp"). In this new version:
[LIST]
[*]The icon blinks while the connection is being established.
[*]The tooltip, while connected, shows the connection ID and time and optionally the output of a user-specified command.
[*]The application can execute a user-specified command at regular intervals.
[/LIST]
I hope this new version will be useful.

---

### Post by say2sky on 2007-10-28
It's convenient and great! Thank you for your efforts. gborzi!:popcorn:

---

### Post by hfdragon on 2007-11-21
Hi, thanks for this great app... but I have a small problem : the icon doesn't stop blinking when the connection is established.. :(

Any idea of what is happening ?

---

### Post by migatxu on 2007-11-21
> **hfdragon said:**
> Hi, thanks for this great app... but I have a small problem : the icon doesn't stop blinking when the connection is established.. :(

Any idea of what is happening ?

Here too, Im using the last version on getdeb

Regards

---

### Post by gborzi on 2007-11-21
> **hfdragon said:**
> Hi, thanks for this great app... but I have a small problem : the icon doesn't stop blinking when the connection is established.. :(

Any idea of what is happening ?

The app icon blinks when it finds the file /var/run/ppp*.pid but the ifconfig pppX command shows that the ppp connection isn't yet active. Basically, the program calls "ifconfig pppX" and counts the number of words in the output. If this number is 37 (which is the number of words shown for an active ppp connection under feisty) it is assumed that the connection is active, otherwise that it isn't.
I suppose that under gutsy the output of ifconfig pppX for an active connection has a different number of words so that the icon continues to blink.
Sorry for this bug, I developed ppptray under feisty, and I haven't yet had the time to test it under gutsy. Surely I need to find a more general method to check active ppp connections.

Thanks for the bug report, I hope to release a fix during the weekend.

---

### Post by migatxu on 2007-11-21
Thank you very much, take all the time you need :)

All the best

---

### Post by gborzi on 2007-11-22
@Migatxu and Hfdragon
Please, can you post the output of > ifconfig pppX where X=number of your active ppp connection.
With this output possibly I can make a better fix.

---

### Post by hfdragon on 2007-11-22
here it is :

```
christophe@christophe-laptop:~$ ifconfig ppp0
ppp0      Lien encap:Protocole Point-à-Point  
          inet adr:10.2.8.100  P-t-P:10.64.64.64  Masque:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          Packets reçus:1912 erreurs:0 :0 overruns:0 frame:0
          TX packets:1857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:3 
          Octets reçus:1979695 (1.8 MB) Octets transmis:251783 (245.8 KB)

```

Hope this can help :)

---

### Post by gborzi on 2007-11-22
Thanks Hfdragon.

---

### Post by praveenpious on 2007-11-22
Thanks :)

---

### Post by gborzi on 2007-11-24
I've made the fix, at least I hope it works as expected. Thanks to Hfdragon i learned that the output of ifconfig varies with the language. The package (v0.2.1) is attached to this post, I'll send the new source to getdeb soon.

---

### Post by andyanderso on 2007-11-24
First of all I really like the idea behind this little program - small, efficient, fast, and reliable.  Thanks for taking the time to write it.  Now for what could be a pretty dumb question:  will it manage a wireless modem like a verizon usb720 -- I am guessing that the answer is yes but I cannot seem to figure out how to configure things so that it works.  Any help?

thanks
andy

---

### Post by gborzi on 2007-11-25
> **andyanderso said:**
> First of all I really like the idea behind this little program - small, efficient, fast, and reliable.  Thanks for taking the time to write it.  Now for what could be a pretty dumb question:  will it manage a wireless modem like a verizon usb720 -- I am guessing that the answer is yes but I cannot seem to figure out how to configure things so that it works.  Any help?

thanks
andy

This app is a GUI for the pon/poff commands, that is to say if you can connect your device with > pon <something> you can use the app.
I use it to connect with my hand phone using GPRS and I have used it with an ADSL USB modem, the DC-204. While searching the net to figure out which kind of device is the verizon usb720, I have found [this page]("http://kenkinder.com/evdo-pc5740/"). It is about a different device of the same class, but if you look at the comments you'll see how to configure the usb720.
Hope this helps.

---

### Post by Turin Turambar on 2007-11-26
Wow! Thanks for this! Better and more easier than gnomeppp!

One suggestion though: it would be better if you could post the newest versions on the first page. Not many people read the entire thread. :)

---

### Post by gborzi on 2007-11-27
Hello Turin,
the app is now available at [www.getdeb.net](www.getdeb.net). Please download it from there, so that I can see how many times it is downloaded.

Regards.

---

### Post by Turin Turambar on 2007-11-28
Done! ;)

---

### Post by _duncan_ on 2007-11-29
Thank you gborzi for the nice app. This lightweight app sure comes in handy particularly since gnome-ppp seems a bit flaky with gutsy 7.10.

---

### Post by JiminyJones on 2007-11-30
you can't use poff/pon without root privileges (running as sudo), therefor the application can't either, which renders it useless. you should either add gksu to the application itself (so it'll ask for a password when you type disconnect) or add gksu to the menu item upon installation.

other than that - very nice app, useful for people who frequently need to reconnect, i actually had 3 launchers for connect/disconnect/reconnect on my panel until i got this program :P.

---

### Post by Turin Turambar on 2007-11-30
I always used pon/poff without sudo! I think you have a problem with privileges.

---

### Post by Cubby on 2007-11-30
Hello Giuseppe and all,

This application you created is just what I have been looking for, but so far I haven't been able to install it.  I am new at using ubuntu and the gnome desktop (3 days) and am more accustomed to KDE desktop after using Mepis for a few months. KPPP dial up utility was great and I miss it.  With ubuntu (system-administration-networking-activate/deactive)  I don't know when I'm connected or disconnected, so that is why your application caught my eye. 

Yesterday I updated all 173 packages that were showing in the package updater.  Ittook all day, but I should be up to date in this respect.   

I downloaded the PPP Tray Icon deb file to my desktop, but when I double click on it (package installer), I get:

*error: dependency is not satisfiable: python gtk-2*

Synaptic shows python2.4-gtk2 is installed

So I downloaded the tar file on my desktop, unpacked it, and couldn't figure out how to install it that way, even after reading the READ ME file.  Yes, I am so new at LINUX, that I have problems trying to figure out what to type in terminal commands, such as sudo, cd, and getting the syntax correct, pointing to the correct package, etc.

I also downloaded gnomePPP and haven't been able to figure out how to install this tar.gz file after unpacking it.  I hear it isn't that great, but was hoping I could get some type of dial up utility installed.  

Thanks for your time!

Lisa Marie
Edited to add that this is what I type in terminal:
user@user-desktop"~$
*sudo python setup.py install* according to the READ ME instructions

and this is what I get:
*python: can't open file 'setup.py': [Errno 2] No such file or directory*

---

### Post by gborzi on 2007-12-01
@JiminyJones
AFAIK you need root privileges for pon/poff only for PPPOE connection, because the eth interface connected to the ethernet modem must be reconfigured for the connection. But you can use network-manager applet to turn on and off a PPPOE connection.
@Cubby
The python-gtk2 version required is 2.10.0 or later. This version introduced support for StatusIcon, i.e. for running programs that go to the system tray.
I don't know if such a version is available in Dapper Drake, sorry. If it isn't, even the manual install will be useless. Speaking of manual install, this is what I should have written in the readme file:> 
Untar the archive
<prompt>$ tar -xzf ppptray-<version>.tar.gz
cd to the newly created directory
<prompt>$ cd ppptray-<version>
install
<prompt>$ sudo python setup.py install


Thanks for your comments, you help me improve the app.

---

### Post by Cubby on 2007-12-01
Thank you gborzi!

I checked, and I do have the latest Python app, so I proceeded with the added information you gave and finally got the syntax correct.  I am happy to say that from the terminal, it appears to have installed itself, or so I think.  Now, I don't know how to bring it up.  I made a dial-up connection using the network connection drop down window in ubuntu and was hoping that would make the PPP Tray Icon appear, but it didn't.  Sorry to pester you with this, as I have found something suitable for now from the "Add to Panel", called Network Monitor Icon.  It's okay.


This is what the terminal showed, which I closed afterward:

[COLOR="DarkSlateGray"]user@user-desktop:~$ cd Desktop/ppptray-0.1
user@user-desktop:~/Desktop/ppptray-0.1$ sudo python setup.py install
Password:
running install
running build
running build_py
running build_scripts
running install_lib
running install_scripts
changing mode of /usr/bin/ppptray to 755
user@user-desktop:~/Desktop/ppptray-0.1$[/COLOR]

I noticed it added a folder named "build" to the ppptrayicon-0.1 file, which includes lib and scripts2-4, so I'm pretty sure I have installed it.  I just don't know how to run it.  Sorry that I need so much hand-holding with installing applications.  Thanks for your time!

Lisa  Marie

---

### Post by gborzi on 2007-12-01
Hello Cubby,
you have installed it successfully. To run it simply type "ppptray" at the command prompt, and an icon should appear in the notification area. Please note that if you want to remove the ppptray-0.1 directory you may need root privileges, i.e. use this command.
> user@user-desktop:~/Desktop $ sudo rm -r ppptray-0.1
Let me know if it works. You can download the latest version 0.2.1 from [www.getdeb.net](www.getdeb.net) .

---

### Post by Cubby on 2007-12-02
Hi gborzi,

Thanks again for helping me with this.  I will add that I am now using wvdial to get my internet connected, as I see that is one of the packages used with PPP Tray Icon.  

I'm almost there, but I get the following after prompt "ppptray":  (I was disconnected when I gave this prompt)

u[COLOR="Navy"]ser@user-desktop:~$ ppptray
Traceback (most recent call last):
  File "/usr/bin/ppptray", line 25, in ?
    ppptray = ppptrayicon.StatusIcon()
  File "/usr/lib/python2.4/site-packages/ppptrayicon.py", line 215, in __init__
    self.status_icon = gtk.StatusIcon()
AttributeError: 'module' object has no attribute 'StatusIcon'
user@user-desktop:~$
[/COLOR]

I will try your latest version to see if I get it correct.  Again, sorry to be such a pest.  Thanks for your time.

Lisa Marie

Edited to add that this is what text editor shows in ppptrayicon.py while connected:

[COLOR="Navy"]class StatusIcon:
   def __init__(self):
      self.status_icon = gtk.StatusIcon()
      self.connected = False
      self.status_icon.set_from_stock(gtk.STOCK_DISCONNECT)
      self.status_icon.set_tooltip("Not connected")
      self.status_icon.connect("popup-menu",self.make_menu)
      self.status_icon.connect("activate", self.on_activate)
      self.readconfig()
      self.cont = True[/COLOR]

At the moment, the page where the the latest version is at is being worked on.  I'll download it in a day or two as soon as they have it back up as I look forward to trying this latest version.  Thanks again.  I'm in no hurry with this.

---

### Post by gborzi on 2007-12-02
Sorry Cubby, your version of python-gtk2 is too old and doesn't support StatusIcon, so ppptray can't work on your system, regardless of its version (I mean of the ppptray version). The output doesn't depend on your connection status, simply the gtk module in python hasn't StatusIcon. You have to upgrade at least to feisty.
Just for the record, ppptray doesn't use wvdial, but pon/poff. You can also configure your dialup internet connection with > sudo pppconf
to monitor your connection status you can use pppstatus > sudo apt-get install pppstatus and run it from the terminal.
Hope this helps.

PS. Don't be afraid of "pesting" me, we are in this forum to ask questions and give answers (well, in case we know the answer).

---

### Post by Cubby on 2007-12-02
Hi gborzi,

It sounds like a great application, and from looking at the screen shots of it, I believe I'll just have to ask my husband to get ubuntu Feisty for me.  I am looking for the distro that suits my needs the best, so this I will have him do.  No problem here, as I've been trying other distros such as Kbuntu Gutsy and as you can see I am familiar with Simply Mepis.

Again, thanks for your precious time!  I did learn a few command-lines, which I really needed to learn how to do, as well as reading up on LINUX.  

I hope to let you know how it works in the future when I get to try it out!  Thanks for the work on it!

Lisa Marie

---

### Post by gborzi on 2007-12-03
Hello Cubby,
do you know that Ubuntu ships CD freely? Look at this [page]("https://shipit.ubuntu.com/").

Regards.

---

### Post by hfdragon on 2007-12-05
I downloaded it, and.... there is still a problem ;)

Now the icon stops blinks when the connection is established... and it disappears !!

I'll keep you advised if I can give more infos about what is happening..

EDIT : Perfectly working on the second try... !!! :):confused:

[B]
EDIT AGAIN :[/B] The icon ha disappeard again, after about 20 minutes of use... and I don't have much infos about that... am I the only one ?

confused:
confused:
confused:

---

### Post by gborzi on 2007-12-05
Hello Hfdragon,
please check if the application is still running when it disappears, for example with this command > ps -ef|grep ppptray if the output is empty it means the application has crashed. If this is the case, please run it from the command line and post the output.
In case it is still running it is possible that the icon in the tray has been covered by some other icon. I have noticed this problem of the notification area some time ago with the compiz tray icon.

Regards.

---

### Post by guhpraset on 2007-12-07
I need to insert some AT commands like this:

AT+CGDCONT=1,"IP","www.xlgprs.net","0.0.0.0"

where should i put it? In gnome-ppp we can put it in setup > init strings.

---

### Post by Crinos512 on 2007-12-07
good question,
I use ATS11=40 to make my modem speed dial.

---

### Post by hfdragon on 2007-12-07
Ok I did run :

> **gborzi said:**
> ps -ef|grep ppptray

An here is the output :

christophe@christophe-laptop:~$ ps -ef|grep ppptray
1000      7243     1  0 19:29 ?        00:00:00 /usr/bin/python /usr/bin/ppptray
1000      7401  7379  0 19:34 pts/0    00:00:00 grep ppptray

So pptray is still running.
I can seen that there a small 'blank' place where the icon is supposed to be. And when I click there, I don't have any response... strange beahaviour... :confused::confused:

---

### Post by gborzi on 2007-12-07
@guhpraset and Crinos512
The init strings cannot be configured in ppptrayicon, you have to change the files in /etc/ppp/peers. This app is only an interface to pon/poff commands, not a configurator for PPP connections. Use pppconf to configure your connections.
@hfdragon
It's really strange. Please post the output of the app when running it from the command line.

---

### Post by Cubby on 2007-12-08
> **gborzi said:**
> Hello Cubby,
do you know that Ubuntu ships CD freely? Look at this [page]("https://shipit.ubuntu.com/").

Regards.

Hi gborzi,

Yes, I knew that they did.  My husband can download it from work with his super-fast connection.  This is no problem for us.  My husband also suggested that since I have the time on my hands to do such things, to see if I can add the lateset GTK+2 version on Dapper Drake - compile it myself.  He gives me much courage.:)

Oh, and thank you for those other command lines to give me information on my connection speed, etc. (pppstatus).  

I did try out Gnome-PPP.  I was able to install it with Automatix2.  It didn't work for me.  

I don't know why I thought PPP Tray Icon required wvdial?  I guess I thought I read it at the .deb download page.  Ups!

Again, take care,
Lisa Marie

---

### Post by say2sky on 2007-12-24
When I run ppptray, I gotten following erro

> ppptray 
Traceback (most recent call last):
  File "/usr/bin/ppptray", line 26, in <module>
    ppptray.main()
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 525, in main
    self.get_info()
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 403, in get_info
    self.init_tip(ppppid[0])
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 370, in init_tip
    f = open( pidfile, 'r' )
IOError: [Errno 13] Permission denied: '/var/run/ppp0.pid'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 71, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_ppptray.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/ppptray", line 26, in <module>
    ppptray.main()
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 525, in main
    self.get_info()
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 403, in get_info
    self.init_tip(ppppid[0])
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 370, in init_tip
    f = open( pidfile, 'r' )
IOError: [Errno 13] Permission denied: '/var/run/ppp0.pid'

I check /var/run/ppp0.pid file's permissions

> 
-rw------- 1 root coolguy 5 2007-12-25 03:42 /var/run/ppp0.pid


After I delete this file, run ppptray again, it's Ok.

I have already set ppptray as a startup program, but it didn't run after reboot so I run it from command line and have above error info. I hope to know what happen?  I have met this issue twice. Thanks for help.

---

### Post by gborzi on 2007-12-24
On my system the permission for /var/run/ppp0.pid are 644, not 600. It looks like you have activated your ppp connection as root and when it was interrupted the .pid file wasn't deleted.
What do you mean when you say that you have set up ppptray as a startup program ? That you put it under System -> Preferences -> Session ?

---

### Post by say2sky on 2007-12-25
> **gborzi said:**
> On my system the permission for /var/run/ppp0.pid are 644, not 600. It looks like you have activated your ppp connection as root and when it was interrupted the .pid file wasn't deleted.
What do you mean when you say that you have set up ppptray as a startup program ? That you put it under System -> Preferences -> Session ?

You are absolutely right I have put it under System -> Preferences -> Session. 
But I don't understand why I have 600 for pid file. I never use sudo to start ppptray.  
And after I delete /var/run/ppp0.pid file, now no more this file when ppptray run. :confused:

---

### Post by gborzi on 2007-12-25
The /var/run/ppp0.pid file is created by ppp, when you invoke pon <your connection>, not by ppptray. When you run ppptray it doesn't create any file in /var/run or any other place besides your home directory where it create its configuration file ~/.ppptrayicon.rc if it doesn't already exist.
As for the 600 mode for /var/run/ppp0.pid, I have no idea of how it can happen.

---

### Post by say2sky on 2007-12-25
> **gborzi said:**
> The /var/run/ppp0.pid file is created by ppp, when you invoke pon <your connection>, not by ppptray. When you run ppptray it doesn't create any file in /var/run or any other place besides your home directory where it create its configuration file ~/.ppptrayicon.rc if it doesn't already exist.
As for the 600 mode for /var/run/ppp0.pid, I have no idea of how it can happen.

Thanks a lot for your help. I have found the 600 mode for /var/run/ppp0.pid is the result of umask in /etc/profile is 077.  I need 077 umask so that the file I create in home directory have 600 permission.  The side effect is that this pid file also have same permission.  :) 

I hope I can find a way to let my own file have 600 but pid will be 640/644.

---

### Post by perixx on 2007-12-25
Hello gborzi,

your script looks most interesting to me! Unfortunately, I've been trying to make it working without success so far....

Installed Python 2.5, as needed. Downloaded the latest source and installed ppptray as stated in the readme-file. When I run '/usr/bin/ppptray' from the terminal, the first time the setup-gui comes up, letting me choose my connection. After acknowledging it, the terminal stays busy forever; hitting CTRL-C will give the following output:
> /usr/bin/ppptray
Traceback (most recent call last):
File "/usr/bin/ppptray", line 26, in <module>
ppptray.main()
File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 526, in main
self.poll()
File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 435, in poll
time.sleep(0.1)
KeyboardInterrupt

I also attempted to 'gksudo' it - no reaction apart from the message above isn't shown, and also no tray-icon shows up...

perixx

---

### Post by perixx on 2008-01-01
no idea at all what could be wrong..?

---

### Post by gborzi on 2008-01-02
With Ctrl-C you kill the application, use Ctrl-Z to send it in the background. Also, you can send the application in the background by adding an & to the command like this > ppptray &
I suggest you to read some basic documentation on the shell.

---

### Post by perixx on 2008-01-02
Hello gborzi, and thanks for reply.

Well, as I said before:
> I also attempted to 'gksudo' it - no reaction apart from the message above isn't shown, ***and also no tray-icon shows up.***..
I thought that 'ppptrayicon' is supposed to do exactly that - giving a tray icon for GUI-access?

> With Ctrl-C you kill the application, use Ctrl-Z to send it in the background. Also, you can send the application in the background by adding an & to the command like this: ppptray &
Allright, I was assuming the script doesn't work since I didn't see any reaction, so I terminated the terminal. Normally, I'd run it with a starter.
It doesn't seem work on my system and I don't know why (I have Xubuntu 7.04). Perhaps you can give me a clue...

perixx

---

### Post by gborzi on 2008-01-03
Sorry, I haven't installed xfce, so I never tried the application with it. I think that xfce has an equivalent of the gnome "Notification area" where the icon should appear. It's the area where you see the network-manager-applet.
on Ubuntu 7.04 I have seen (very rarely) that a new icon in the gnome notification area goes under an already existing icon, so that one cannot see it.

---

### Post by perixx on 2008-01-03
Hello again and thanks for the hint with the 'notification area'!

Indeed, there was no 'System tray' added to my panel bar - after setting it up and starting your script, the plug-symbol were showing up! Unfortunately, after clicking on it once, the symbol vanished and the terminal gave the following output:
> Plugin rp-pppoe.so loaded.
Traceback (most recent call last):
  File "/usr/bin/ppptray", line 26, in <module>
    ppptray.main()
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 526, in main
    self.poll()
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 433, in poll
    self.get_info()
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 403, in get_info
    self.init_tip(ppppid[0])
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 378, in init_tip
    stdout=subprocess.PIPE,stderr=subprocess.PIPE).communicate()[0]
  File "/usr/lib/python2.5/subprocess.py", line 593, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1135, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

After that, I couldn't re-launch the app anymore (haven't rebootet yet, though)...

perixx

---

### Post by gborzi on 2008-01-03
It seems that you have configured ppptray in such a way that it should put the output of a command in the tooltip, i.e. "Tooltip also shows the output of:". Which is this command?

---

### Post by perixx on 2008-01-03
Hi!

For I couldn't start the script, I searched and was able to find the used text in '~/ppptrayicon.rc':
> DSL-Verbindung

After renaming the file, I could re-configure the script without tooltip and it's been running fine since then!

For verification, I've inserted another tooltip-text:
> Netzwerk an/aus
with the same crashing issue, so. Then I figured, maybe the script doesn't like special chars and only inserted 'dsl'...
it didn't produce any visible effect, but kept the script from crashing again.

On a second thought, maybe this feature was supposed to apply some special options or the likes? Anyway, I simply spared the tooltip-section for now.

Seems to run great now..!
Many thanks for this nifty little app :)

Btw., did you think of adding some net-traffic display and/or blinking icon when traffic is taking place (I may have missed something here, but perhaps it's already availible in Gnome/KDE...)? 
Is there by any means a possibility to also let the script also disconnect the LAN-connection to the DSL-modem/router for a complete networking halt?

perixx

---

### Post by gborzi on 2008-01-03
Please note that the configuration dialog says "Tooltip also shows the output of:", that means you have to put a command that can be executed in a terminal and its output will be displayed in the tooltip while the connection is active. For example, if you want to see the IP address of the ppp connection you add the command > pppstatus --ipaddress in the text entry box associated with "Tooltip also shows the output of:". Obviously you need to install pppstatus, which is not installed by default. This command is executed when the connection is established, it is not repeated while the connection is on.
In case you want to see the text "DSL-Verbindung" or "Netzwerk an/aus" in the tooltip simply use > echo -n "DSL-Verbindung" or > echo -n "Netzwerk an/aus"
When there isn't a ppp connection, the tooltip only shows "Not Connected".
As for displaying net traffic, I will not add this feature, there is already the system monitor applet in Gnome, don't know in Xfce.

---

### Post by perixx on 2008-01-04
Well, seems to be a nice feature! But when inserting the command
```
pppstatus --ipaddress
```
into the upper field, as you stated, I get the immediate result of a crash (and the terminal output):
>  ppptray
Traceback (most recent call last):
  File "/usr/bin/ppptray", line 26, in <module>
    ppptray.main()
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 525, in main
    self.get_info()
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 403, in get_info
    self.init_tip(ppppid[0])
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 378, in init_tip
    stdout=subprocess.PIPE,stderr=subprocess.PIPE).communicate()[0]
  File "/usr/lib/python2.5/subprocess.py", line 593, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1135, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
 
Inserting ```
echo -n "DSL-Verbindung"
``` worked upon the next start, though. I wondered why and figured out that 'pppstatus' wasn't installed on my system - so there's no wondering why it didn't work :)

But you might add some error-catching routine to handle such exceptions without making the script exiting, maybe...

Thank you for your help!

perixx

---

### Post by gborzi on 2008-01-04
> **perixx said:**
> 
But you might add some error-catching routine to handle such exceptions without making the script exiting, maybe...

Thank you for your help!

perixx
You are right, the app needs a complete error-management implementation, perhaps I'll do it for release 0.3, provided I'll have the time.
Also, I need to improve the documentation, you're not the only one that misunderstood how to use the "Tooltip also shows the output of:" entry.

Thanks for the feedback.

---

### Post by Mohammad.Mnt on 2008-01-09
BUG: pppTray is vanished when the kicker is restarted
Kubuntu 7.10 + KBFX installed as a KDE Menu

---

### Post by Crinos512 on 2008-01-09
Another use of the "Tooltip also shows the output of:" section is to display the connection speed of your modem.

[COLOR="Blue"]**_process_**[/COLOR]
1. run **sudo pppconfig**, and under "Advanced" change your Initialization string to read **ATW2S11=40** Explained below:
>   **AT** >> attention modem
  **W2** >> report connection speed
  **S11=40** >> set number of milliseconds between digits when dialing (speed dial)
2. add the following line into the "Tooltip also shows the output of:" section:
**grep 'CONNECT' /var/log/syslog | tail -n1**

**_NOTE_**: this *should* work, but some modems do not support the **W2** initialization string, ...also this line will probably need trimming down with the **cut** command as well.

Let me know what you think! :D

---

### Post by gborzi on 2008-01-10
@Crinos512
This is the use of "Tooltip also shows the output of:" I had in my mind when I implemented it. If you agree, I'll add your post to the README file and the manpage of the next version.
@Mohammad.Mnt
Thanks for the bug report. Unfortunately I'm not able to reproduce the bug (so as to fix it), because I don't have KDE installed.

---

### Post by Crinos512 on 2008-01-11
I whole heartedly agree. :D

and to think, I've only been using Linux for ~6 months, and I get quoted in a manpage... sweet!

---

### Post by say2sky on 2008-06-06
is it possible to have a choice to show the connect icon or ip address in the future version?

---

### Post by Crinos512 on 2008-06-07
@Say2Sky: try adding the following line into the "Tooltip also shows the output of:" section:

**ifconfig ppp0 | head -n2 | tail -n1**

---

### Post by say2sky on 2008-06-07
> **Crinos512 said:**
> @Say2Sky: try adding the following line into the "Tooltip also shows the output of:" section:

**ifconfig ppp0 | head -n2 | tail -n1**

thanks a lot for your help. 

after I input **ifconfig ppp0 | head -n2 | tail -n1**    into **Tooltip also shows the output of** section,  OK button is useless ie. it cannot be used to close the small "configure PPP Tray Icon" window.   is there any clue about this situation?

---

### Post by gborzi on 2008-06-07
Hello say2sky,
on my system the OK button works as expected. Please start ppptray from the command line and report any output it gives.

---

### Post by say2sky on 2008-06-07
> **gborzi said:**
> Hello say2sky,
on my system the OK button works as expected. Please start ppptray from the command line and report any output it gives.

Thanks a lot for your help.

```

:~$ ppptray 
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 297, in bwriteconfig
    self.writeconfig()
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 286, in writeconfig
    f = open( file, 'w' )
IOError: [Errno 13] Permission denied: '/home/say2sky/.ppptrayicon.rc'

```


Then I do
```

sudo chown  say2sky:say2sky .ppptrayicon.rc

```

Now I have
```

:~$ ls -la .ppptrayicon.rc 
-rw------- 1 say2sky say2sky 221 2008-06-08 05:42 .ppptrayicon.rc

```

try again
```

:~$ ppptray 
Traceback (most recent call last):
  File "/usr/bin/ppptray", line 26, in <module>
    ppptray.main()
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 525, in main
    self.get_info()
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 403, in get_info
    self.init_tip(ppppid[0])
  File "/usr/lib/python2.5/site-packages/ppptrayicon.py", line 370, in init_tip
    f = open( pidfile, 'r' )
IOError: [Errno 13] Permission denied: '/var/run/ppp0.pid'

```

```

ls -la /var/run/ppp0.pid 
-rw------- 1 root say2sky 6 2008-06-08 06:25 /var/run/ppp0.pid

```

---

### Post by say2sky on 2008-06-07
update info

Now I change my system permission setting.

```

ls -la .ppptrayicon.rc 
-rw-r--r-- 1 say2sky say2sky 256 2008-06-08 06:56 .ppptrayicon.rc

```


```

ls -la /var/run/ppp0.pid 
-rw-r--r-- 1 root say2sky 6 2008-06-08 06:25 /var/run/ppp0.pid

```

now I run ppptray at command line, no error info show. but still no tooltip ip is showed when mouse is on ppptray icon on gnome-panel

---

### Post by gborzi on 2008-06-07
When you are connected through ppp, which is the output of 
```
ifconfig ppp0 | head -n2 | tail -n1
```
note that you have to mark the Checkbutton to the left of "Tooltip also shows...".

---

### Post by say2sky on 2008-06-07
> **gborzi said:**
> When you are connected through ppp, which is the output of 
```
ifconfig ppp0 | head -n2 | tail -n1
```
note that you have to mark the Checkbutton to the left of "Tooltip also shows...".

```

ifconfig ppp0 | head -n2 | tail -n1
          inet addr: xxx.xxx.28.214  P-t-P:xxx.xxx.0.246  Mask:255.255.255.255


```

I indeed mark the checkbutton. 
now My tooltip show

```

Connection ID: dsl-provider
Connection Time: Connection Time: xxh xxm xxs
+one empty line here

```

---

### Post by say2sky on 2008-06-07
do I need to put 

```

ifconfig ppp0 | head -n2 | tail -n1

```

into section of execute command and mark the checkbox left? now I indeed also input this. but tooltip is same.

---

### Post by gborzi on 2008-06-07
I think that the problem is due to the fact that the command is executed too soon, i.e. when /var/run/pppX.pid is created the command is executed, but the ppp connection hasn't yet established, and the above command doesn't give any output. Maybe I should add an optional delay for the tooltip command.

---

### Post by say2sky on 2008-06-07
> **gborzi said:**
> I think that the problem is due to the fact that the command is executed too soon, i.e. when /var/run/pppX.pid is created the command is executed, but the ppp connection hasn't yet established, and the above command doesn't give any output. Maybe I should add an optional delay for the tooltip command.

Thanks for your help. waiting for your solution.

in the preference window there is a poll interval setting does this can help out?

---

### Post by Crinos512 on 2008-06-07
How about:

**sleep 5 && ifconfig ppp0 | head -n2 | tail -n1 | head -c34 | tail -c24**

---

### Post by Mach1US on 2008-06-23
This worked for me :)

---

### Post by Crinos512 on 2008-06-23
Sweet! glad to hear it! 

:D

---

