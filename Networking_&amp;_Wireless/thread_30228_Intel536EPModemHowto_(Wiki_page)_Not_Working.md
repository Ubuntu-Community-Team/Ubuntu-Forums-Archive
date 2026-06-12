---
title: "Intel536EPModemHowto (Wiki page) Not Working"
date: 2005-04-27
forum: Networking &amp; Wireless
---

### Post by Zerksis on 2005-04-27
Follow the link below to a new improved post, in this forum.

*Intel536ep Modem, Working, Wiki, Whoops - Newbie Win*

[http://ubuntuforums.org/showthread.php?t=37465](http://ubuntuforums.org/showthread.php?t=37465)

Hope this helps.

Z

---

### Post by az on 2005-04-27
As a rule, these modems work with the sl-modem driver, too.

You need the daemon and the module packages:
[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)

---

### Post by Zerksis on 2005-04-28
Hi azz,
             First, many thanks for the reply, appreciated.

Tried your suggestion - (which rule was that) - sorry did not work.
Downloaded the 2 files;-

sl-modem-daemon_2.9.9a-1ubuntu2_i386.deb
sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb 

thought the cmd. looked so easy to run both;-

dpkg -i sl-modem*.deb

but it failed with;-

Selecting previously deselected package sl-modem-daemon.
(Reading database ... 58010 files and directories currently installed.)
Unpacking sl-modem-daemon (from sl-modem-daemon_2.9.9a-1ubuntu2_i386.deb) ...
Selecting previously deselected package sl-modem-modules-2.6.10-5-386.
Unpacking sl-modem-modules-2.6.10-5-386 (from sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb) ...
Setting up sl-modem-modules-2.6.10-5-386 (2.9.9a-1ubuntu2+2.6.10-34) ...
[COLOR=Green]#####[/COLOR]
/var/lib/dpkg/info/sl-modem-modules-2.6.10-5-386.postinst: line 27: /etc/init.d/sl-modem-daemon: [COLOR=Blue]No such file or directory[/COLOR]

[COLOR=Green]#####  line 27= /etc/init.d/sl-modem-daemon start || true[/COLOR]

Setting up sl-modem-daemon (2.9.9a-1ubuntu2) ...
Loading ALSA modem driver into kernel ... done.
Starting SmartLink Modem driver for: .
Creating /dev/modem symlink, pointing to: /dev/ttySL0.

However, this time the file referred to - /etc/init.d/sl-modem-daemon - does exist!
-----------------------------------------------------------------------------------

So, what gives?  does Ubuntu 5.04 just hate analog modems!
I mean, I had to modify /ect/ppp/peers/ppp0 to add 115200 to get a simple serial modem to work.  Even then the monitor does not tell me what speed I'm conneced at (I need that.) 

Are we making assumptions that are not true?
I installed the above by wiping HD & doing a clean re-install, so that nothing should be screwed up by anything that was previously modified.
Did not install build essential linux-headers - were these req?
Loaded files & ran dpkg...

What now ?

regards,   Z

---

### Post by az on 2005-04-28
To make sure that the packages are installed properly (they seem to be, despite the error) do

sudo apt-get -f install


If you still have the packages installed, do

sudo dpkg-reconfigure sl-modem-daemon 

and make sure that it is not using the alsa driver, but the slamr driver (slmodem)

You can tell by doing

sudo /etc/init.d/sl-modem-daemon restart
and looking at the output.

---

### Post by Zerksis on 2005-04-28
Seems pkg. not installed.

apt-get -f...        o/p  is;-

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Z

BTW the earlier file shows;-

Loading [COLOR=Blue]ALSA [/COLOR]modem driver into kernel ... done.

---

### Post by az on 2005-04-29
"Seems pkg. not installed.

apt-get -f... o/p is;-

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

Actually, that would mean they _are_ installed.



"BTW the earlier file shows;-

Loading ALSA modem driver into kernel ... done."

Right, which is why you should do 
sudo dpkg-reconfigure sl-modem-daemon 
to toggle from the alsa driver to the slamr driver.

---

### Post by sancho on 2005-04-29
hey man.  
I have sucessfully gotten my Intel536 modem to work under 5.04 using the walktrhough and the intel sources.  

here is the basic steps i used 

```
*modem - Inel 536ep
   download drivers source uncompiled.   intel-536ep-4.69.1.tgz
  extract 
    tar -xzvf intel-536ep-4.69.1.tgz  
     cd intel-536EP-2.56.76.1/
     patch -l -p1 < ~/intel536.diff
     ##(or) patch -l -p1 < <directory-where-diff-is>/intel536.diff
     sudo make clean
     sudo make 536
      sudo cp Intel536.ko /lib/modules/$(uname -r)/misc
      sudo depmod -a
      sudo modprobe Intel536  ##insmod instead of modprobe if necessary
      sudo echo Intel536 >> /etc/modules   ##or vim /etc/modules and add it manually if necessary
      device is /dev/536ep0   

``` 

looking at your post it seems like the drivers are made properly.   There are some warnings in the build, so its 'safe' to ignore some of them.   

Are you sure you patched the drivers correctly?  Did you get a message about x number of lines fuzzy?

next...the cp command does copy it to a 'misc' device.    Not sure why they set it up that way but it works.   I've never seen a fatal error when copying something. After i do the copy i do a depmod, an insmod, and vim the /etc/modules file.   I noticed some of those steps didn't quite work right for me.  

Please post back more detailed errors.   Perhaps a sudo tail /var/log/messages as well and i'll try my best to help you.

---

### Post by Zerksis on 2005-04-29
Tried azz's reconfig driver, result;-

:~$ sudo dpkg-reconfigure sl-modem-daemon
Password:
Shutting down SmartLink Modem driver normally ... no slmodemd daemon running.
Loading ALSA modem driver into kernel ... done.
Starting SmartLink Modem driver for: .
Creating /dev/modem symlink, pointing to: /dev/ttySL0.

:~$

No ttySL0 found in modem list & if I select dev/modem it still does
not do anything.   

Azz, what have I done wrong here ?  

---------------------------------------- 

Sancho,
Thanks for the offer - I'm intrigued that you have yours working by using the Wiki-HowTo.  

So what is your MB & proc ?
Mine is Asus P4S800D-E Delux with 2.6GHz - 800MHz FSB - P4 and 1GB ram.  So there should be sufficient resources.

I will wipe HD do a clean install, no network, as I just use a Xover cable to laptop.  (can't wait to try getting Ubuntu working the laptop modem!)

I think we ought to try to get it working by the Wiki HowTo if poss.
Then I can post a Wiki WORKS  (red face!)  after all that is how most new users will start.

Later guy's

Z

---

### Post by az on 2005-04-29
You using the Hoary stock kernel?

---

### Post by Zerksis on 2005-04-29
azz,
 Whatever kernel is on the Hoary iso, and the default install uses.

Sancho,
  No msg. about "n lines fuzzy"
           
Z

---

### Post by Zerksis on 2005-04-30
More Info.

Now this is interesting;-  



root@ubuntu04:/home/test4 # tail /var/log/messages

Apr 30 14:05:17 localhost gconfd (test4-7472): Resolved address "xml:readwrite:/ home/test4/.gconf" to a writable configuration source at position 1
Apr 30 14:05:17 localhost gconfd (test4-7472): Resolved address "xml:readonly:/e tc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr 30 14:05:17 localhost kernel: NET: Registered protocol family 10
Apr 30 14:05:17 localhost kernel: Disabled Privacy Extensions on device c02f0500 (lo)
Apr 30 14:05:17 localhost kernel: IPv6 over IPv4 tunneling driver
Apr 30 14:05:25 localhost gconfd (test4-7472): Resolved address "xml:readwrite:/ home/test4/.gconf" to a writable configuration source at position 0
Apr 30 14:09:35 localhost gconfd (root-7754): starting (version 2.10.0), pid 775 4 user 'root'
Apr 30 14:09:35 localhost gconfd (root-7754): Resolved address "xml:readonly:/et c/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr 30 14:09:35 localhost gconfd (root-7754): Resolved address "xml:readwrite:/r oot/.gconf" to a writable configuration source at position 1
Apr 30 14:09:35 localhost gconfd (root-7754): Resolved address "xml:readonly:/et c/gconf/gconf.xml.defaults" to a read-only configuration source at position 2

**** after trying insmod and echo 
     this turned up in tail... !

Apr 30 14:23:44 localhost kernel: Intel536: [COLOR=Red]module license 'Proprietary' taints kernel.[/COLOR]

root@ubuntu04:/home/test4 #

*** FILE LIST

test4@ubuntu04:/home/intel-536EP-2.56.76.1$ ls

config_check  hamregistry    Intel536_inst  license.txt  readme.txt
coredrv       Intel536_boot  Intel536.ko    makefile

test4@ubuntu04:/home/intel-536EP-2.56.76.1$



Not impressed!

Z

---

### Post by az on 2005-04-30
"Apr 30 14:23:44 localhost kernel: Intel536: module license 'Proprietary' taints kernel."

Yup.  The sl-modem driver is not GPL.  That is all that the message means.  I beleive that there are other messages when the module loads?  What are they?  That would be helpful to know why your driver is not working.

---

### Post by Zerksis on 2005-05-01
azz,  Hi, did not expect you today.  Or is the snow heavy ?

Have you looked at the attachment I added to an earlier post - is the info. you need not there ?  8Kb of text captured from terminal as I did the install.  That was the last entry in "tail" nothing edited out.

I would have added it as sancho did (code?) but I was not sure how to do that - so it became an attachment  :roll: 

One small point, (clutching at straws!), as I do not have a modem working in Ubuntu - file downloads were done on WinXP.  In XP I use a "limited" a/c (not one with administrator rights) to access the internet.  [same as *not* logging on as "root" really] 

When I came to copy the files into my Linux home dir., from the USB key, I could not because of "permissions".
So I granted both the files "all" with chmod and the files in the uncompressed folder.

How would you deal with this situation.  

BTW bought O'Reilly (pub) "Linux in a Nutshell",  good.  

Z

---

### Post by Zerksis on 2005-05-02
azz, sancho,

OK - I now know that Linux will run the PCI modem with my hardware.

I just loaded up Xandros 3.01 - it simply recognised the Intel 536 card, loaded drivers for it & configured it.  

I was able to browse using FireFox, & read Thunderbird Email in about 35min from start of loading, even though it seemed to think it a 14k Fax modem.  

So if we cannot get ubuntu to work in the next replies - then forget it.   I may look at it again in the next release.

Now I'm off to check out Mepis (Debian based too).   

I just cannot waste so much time trying to get a $14 modem to work!

To me this result means that Ubuntu is not yet ready to support Win  users with analog PCI modems - even if the modem mfg. claims Linux support.  Access to Email & the Internet via analog modems is a pretty important part of any OS that hopes to get widespread support.  If I cannot get this analog modem to work then what chance is there that I could get Ubuntu to run my PCTel Winmodem in my ECS portable, (and it cannot be changed like the PCI modem.)

Pity, because I really like Ubuntu - however,  one has to be practical.

Many thanks, in advance, for all the replies and your time.

Best regards,
                     Z

---

### Post by az on 2005-05-03
"So if we cannot get ubuntu to work in the next replies - then forget it. I may look at it again in the next release.

Now I'm off to check out Mepis (Debian based too). 

I just cannot waste so much time trying to get a $14 modem to work!

To me this result means that Ubuntu is not yet ready to support Win users with analog PCI modems - even if the modem mfg. claims Linux support. Access to Email & the Internet via analog modems is a pretty important part of any OS that hopes to get widespread support. If I cannot get this analog modem to work then what chance is there that I could get Ubuntu to run my PCTel Winmodem in my ECS portable, (and it cannot be changed like the PCI modem.)

Pity, because I really like Ubuntu - however, one has to be practical."

I am certain than there were Xandros users or Mepis users that had the same problems you do, but with the opposite attitude.  I am certain that one of them filed a bug report detailing the efforts that were made to get the device working and outlining the problem.
These users need not have been experts, just people who contribute to the community instead of whining.

bugzilla.ubuntu.com

If there is mention of your troubles already there, add to the report.  If not, start one of your own and follow up on it (linux-image package, there is no reason why the driver should not work with the ubuntu kernel).

---

### Post by Zerksis on 2005-05-03
azz,
      Hmmm, my, my, we are touchy.
      
Sorry if you interpret the following statements (of facts);-
 
[COLOR=Blue]"To me this result means that Ubuntu is not yet ready to support Win users with analog PCI modems - even if the modem mfg. claims Linux support.
 
Access to Email & the Internet via analog modems is a pretty important part of any OS that hopes to get widespread support... "[/COLOR]

as whining with a bad attitude.  
Are you sure you understand the meaning of the word "Moderator" ?

As Xandros 3.01 just recognised the Intel 536 modem and installed it, my comments are quite clearly fact, whether you like it or not.

Furthermore, just to put you straight, the purpose of my checking out other distributions was to compare Ubuntu with more than one other system that would install the 536 modem, (2 is better than 1.)  By comparing configuration files I hoped to be able to post some helpful facts.  From what I read Xandros is not derived from Debian whereas Mepis is, hence if Mepis does install the 536 modem any config info would possibly be of more use to Ubuntu users. 

Z

---

### Post by az on 2005-05-03
You have obviously misunderstood me.  I do not care what OS you use.  I have given you my time and effort to try and fix your problem.  It would be nice if you tried to give back.

"As Xandros 3.01 just recognised the Intel 536 modem and installed it, my comments are quite clearly fact, whether you like it or not."

I am sure that it is also recognised in Windows.  I know your hardware works.  I would like to see the problem solved in Ubuntu.  It would be nice if you contributed to Ubuntu by filing a bug report and followed up on it.


"From what I read Xandros is not derived from Debian whereas Mepis is, hence if Mepis does install the 536 modem any config info would possibly be of more use to Ubuntu users."

Again, you misunderstood what you read.  Both Xandros and Mepis are derived from Debian.



"Are you sure you understand the meaning of the word "Moderator" ?"


Please avoid being provocative.  Let's focus on fixing the problem.

---

### Post by sancho on 2005-05-09
Zerksis;

hey man.  sorry i've been out of it for a while.  
Also, i'm sorry you are having so many trouble and i hope that you have not given up on ubuntu.  

First off you need build essential installed.  Then you also need kernel-source and kernel headers.  Be sure to extract the kernel source under /usr/src and a "linux" symlink to the extracted folder might be necessary.  I think the howto covered this but i'm not sure.   Then you extract the intel drivers and apply the patch.  Upon applying the patch you should get the   "fuzzy lines" message.  If you do not see this message the patch was not applied properly and the drivers will never build properly.   

If you are still around please post EVERYTHING the machine says while you do the make clean, make 536, make install.   That way i can see if the drivers are ever being made properly.

---

### Post by sancho on 2005-05-09
sorry i'm an idiot.  Upon glancing over the posts again i see that you attached the output.   


Your driver is not being compiled properly, because it is not being patched right.   There is no fuzzy lines.   

notice the "ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed to build driver"   line that confirms my belief.  

The /home/intel536.diff  
needs to contain this 
```

diff -ur intel-536EP-2.56.76.1/coredrv/softserial.h intel-536EP-2.56.76.1-vedran/coredrv/softserial.h
--- intel-536EP-2.56.76.1/coredrv/softserial.h  2004-10-15 10:16:53.000000000 +0200
+++ intel-536EP-2.56.76.1-vedran/coredrv/softserial.h   2005-01-22 18:51:32.000000000 +0100
@@ -86,7 +86,7 @@
 int  softserial_open           (struct tty_struct*, struct file*);
 void softserial_put_char       (struct tty_struct*, unsigned char);
 void softserial_set_termios    (struct tty_struct*, struct termios*);
-int  softserial_write          (struct tty_struct*, int, const unsigned char*, int);
+int  softserial_write          (struct tty_struct*, const unsigned char*, int);
 int  softserial_ioctl          (struct tty_struct*, struct file*, unsigned int, unsigned long);


Only in intel-536EP-2.56.76.1-vedran/coredrv/: softserial.o
diff -ur intel-536EP-2.56.76.1/coredrv/softserial_io.c intel-536EP-2.56.76.1-vedran/coredrv/softserial_io.c
--- intel-536EP-2.56.76.1/coredrv/softserial_io.c       2004-10-15 16:00:42.000000000 +0200
+++ intel-536EP-2.56.76.1-vedran/coredrv/softserial_io.c        2005-01-22 18:51:17.000000000 +0100
@@ -55,7 +55,6 @@
 //=============================================================================
 static DECLARE_MUTEX(softserial_write_sem);
 int softserial_write(struct tty_struct* ptty,
-                      int from_user_space,
                       const unsigned char* input_buffer,
                       int write_count_asked)  //why is it a signed int?
 {
@@ -73,41 +72,6 @@
    //printk("softserial:softserial_write()\n");
    //printk("write: fus%d, count%d\n",from_user_space, write_count_asked);

-   if(from_user_space)
-   {
-      down(&softserial_write_sem); //this may not be enough
-      while(write_count_asked - written_count > 0)
-      {
-         softcore_space = G.softcore.write_free();
-         if(softcore_space == 0) break;  //try again?  potential infinite loop?
-         //printk("space free %d\n",softcore_space);
-
-         if(write_count_asked > softcore_space)
-         {
-            copy_size = softcore_space;
-         }
-         else
-         {
-            copy_size = write_count_asked;
-         }
-
-         copy_from_user(G.softcore.tx_fifo, input_buffer_ptr, copy_size);
-         //printk("tx_fifo[0]=%c copysize=%d",*(G.softcore.tx_fifo),copy_size);
-       // if(copy_size <= 0)
-        // {
-        //    return(-EFAULT);
-        // }
-
-
-         G.softcore.write(copy_size);
-
-         input_buffer_ptr += copy_size;
-         written_count += copy_size;
-      }
-      up(&softserial_write_sem);
-   }
-   else           //data is from kernel space
-   {
       while(write_count_asked - written_count > 0)
       {
          softcore_space = G.softcore.write_free();
@@ -127,7 +91,6 @@
          input_buffer_ptr += copy_size;
          written_count += copy_size;
       }
-   }

    return(written_count);
 }

```


Also, are you sure that you had the path to the file right?  
try this command    :
patch -l -p1 < <directory-where-diff-is>/intel536.diff
put the FULL in place of the <...>.       Just another observation you were doing this from you /home/ directory.   Most people save things to /home/<user>/intel536.diff for instance.   Maybe it was just a simple typo.

---

### Post by Zerksis on 2005-05-10
Sancho,

Hi, many thanks for your helpful comments.  I really appreciate the 
"one-on-one" offer of help.

There is good news!  I have it [COLOR=DarkGreen]working...[/COLOR] :grin: 

So - no I have not given up on Ubuntu.

I will write up some notes on what I found and post it in a new thread,  this will save any interested users having to trawl through a heap of confusing dead ends. I'll include the terminal file so everyone can look at what was done.
----------------------------


I went to "[COLOR=Blue]linmodems.technion.ac.il[/COLOR]" and found a copy of 

*"Compiling drivers for newbies"*

and noted that;-

"[I]They are commonly compiled as Modules and installed as ModuleNames.o
into sub-folders of;  /lib/modules/kernel-version/[/I]"

and;-
"[I]3. the modules will be installed by:
            make modules-install
    to sub folders of /lib/modules/[/I]
							
Also ..., in the Intel 536ep "ReadMe" file it states;

[I]4. FILE DESCRIPTIONS
...
files copied to /lib/modules/(kernel-version)/[COLOR=Red]misc[/COLOR]
    Intel536.o(Intel536.ko) modem driver.[/I]
    
So it is pretty obvious that a folder /lib/modules/(kernel-version)/misc has to exist before installing the Intel536.ko file and running copy commands.

Once I created this folder at the start, the driver install process then worked.

You were right about putting the full path in the patch cmd, but that was not the problem. Because each time it failed I did as you (& the Wiki) suggested and used <dir where .diff is> 
More on this in the new thread.  

As I queried the "misc" folder in the first post it is a pity that the significance this was not understood.  

It was your comment that you have it working "using the walk-through & the Intel sources" and that the cp cmd "does copy it to a 'misc' device" that focussed my attention on the investigation path (excuse the pun!) I took. 
   
Thanks again for your comments.

Best regards,
                      Z

---

### Post by sancho on 2005-05-13
no problem man.   

glad to hear you got it working.  

got a link to that new thread?

---

### Post by Zerksis on 2005-05-18
Sancho,
              Have not finished writing it yet - been away & have to go away again for next 2 wks.
Will get round to it as soon as I can.

Need to wipe disk & redo the modem install, just to make sure that the whole process is repeatable.  

Will post here again when done.

regards,
               Z

---

### Post by Zerksis on 2005-05-27
Sancho,

I have posted the details of the steps I took to get the Intel536 Winmodem working.

It's in this (Networking) forum, title is;-

*Intel536ep Modem, Working, Wiki, Whoops - Newbie Win*

[http://ubuntuforums.org/showthread.php?t=37465](http://ubuntuforums.org/showthread.php?t=37465)

This should help others, without going down a string of dead ends - as this thread did.

Will delete this thread, as it's confusing, later.

Z

---

