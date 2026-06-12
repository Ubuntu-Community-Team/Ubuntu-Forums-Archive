---
title: "Speedtouch 330 + Edgy"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by diskjunky on 2006-10-23
Ive been using Kubuntu for about 5 months and im really enjoying the experience. I originally started with breezy and setup my speedtouch modem using the speedtouchconf script all went well and it worked with no probs what so ever....i then upgraded to dapper and the speedtouch install went fine....yesterday i decided to try out edgy and when i tried to install the speedtouch i got a modem_run 253 error which say the modem was not found where expected. Has anyone managed to get the speedtouch to work with edgy yet? I know my best bet would be to get an ethernet modem but funds do not permit at the moment! Any help would be greatly appreciated.

---

### Post by fishpie on 2006-10-26
Hi,

I've been running my speedtouch modem with edgy using PPP over ATM since knot1 and have had no problems. I have never used speedtouchconf so I can't help you with that. However, I can tell you how I managed to set it up. I followed most of the instructions from: [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html")

These instructions are for dapper but have worked fine for me with edgy. Since my ISP uses PPP over ATM, I have not tried the instructions for PPPoE so I cannot guarantee that they will work. I do not use the boot script provided. A neater solution is to place the following lines in your /etc/network/interfaces file

```
auto speedtch
iface speedtch inet ppp
provider speedtch
```

Your modem should now automatically connect to internet when you boot.

Despite my modem working properly I used to get a couple of annoying warning messages about loading firmware whenever I booted. Creating a couple of symbolic links using the following commands solved the problem

```
cd /lib/firmware
sudo ln -s speedtch-1.bin speedtch-1.bin.2.00
sudo ln -s speedtch-2.bin speedtch-2.bin.2.00

```
I hope that this advice helps you. It has been a while since I installed edgy so I might have forgotten something. If you follow this advice and still have problems please post again and I'll do my best to help.

---

### Post by fishpie on 2006-10-26
speedtouchconf only works with kernels up to 2.6.10 and edgy uses 2.6.17.  I recommend removing your speedtouchconf settings with undo.sh and then following the instructions in my previous post

---

### Post by diskjunky on 2006-10-26
Thanks worked perfectly!!!

---

### Post by mwob on 2006-10-28
Hi,

I am in the same boat - I installed Ubuntu edgy as a clean re-install, and found that I couldn't use the speedtouchconf script.

I tried following the instructions that were given on this page, and can't get the firmware-extractor to work :( Here's the output from Ubuntu:

matt@button:~$ unzip SpeedTouch330_firmware_3012.zip && chmod +x firmware-extractor && ./firmware-extractor ZZZL_3.012
Archive:  SpeedTouch330_firmware_3012.zip
  inflating: KQD6_3.012              
  inflating: ZZZL_3.012              
**bash: ./firmware-extractor: **No such file or directory

Heres a folder listing:

matt@button:~$ ls
Desktop   firmware-extractor  KQD6_3.012  SpeedTouch330_firmware_3012.zip
Examples  Important           modem_run   ZZZL_3.012

For some reason firmware-extractor complains, even though it is there, is executable, and the file "ZZZL_3.012" exists.

Please can someone help? I can't get tinternet !

---

### Post by fishpie on 2006-10-28
Hi mwob,

Your problem is very puzzling. The error message that you have received suggests that there is no firmware-extractor file in your current directory. My best advice is to have another go with ```
./firmware-extractor ZZZL_3.012
``` if this does not work do the following command and post the result here
```
ls -l
```

---

### Post by Feline on 2006-10-29
i've the same problem. but i use KQD6_3.012 

the strange think is that i have firmware extractor in home folder, but it seems that d'ont recognize that file.

please help me ^^

and sorry for my english, i am italian^^

bye and thanks

---

### Post by fishpie on 2006-10-29
Hi Feline,
Are you using the command > ./firmware-extractor KQD6_3.012 and not > firmware-extractor KQD6_3.012 ? Including the "./" is important. If you are still having problems post exactly what you typed in and exactly what the result was, followed by the result of "ls -l" and I should be able to help

---

### Post by mwob on 2006-10-29
Hi fishpie,

Thanks for the suggestions, but I've had no luck with them. I can confirm that both the FE and the ZZZ file exist in my home folder, but I still get the "unknown file or directory" error when I run the firmware-extractor. As requested, here's the output from ls -l:

```

matt@button:~$ ls -l
total 2296
drwxr-xr-x 2 matt matt   4096 2006-10-26 21:03 Desktop
lrwxrwxrwx 1 matt matt     26 2006-10-26 21:54 Examples -> /usr/share/example-content
**-rwxr-xr-x 1 matt matt  11901 2006-10-28 14:41 firmware-extractor**
drwxr-xr-x 4 matt matt   4096 2006-10-28 15:11 Important
-rw-rw-rw- 1 matt matt 763677 2004-03-05 12:03 KQD6_3.012
-rw-r--r-- 1 matt matt    462 2006-10-28 10:11 modem_run
-rwx------ 1 matt matt 769125 2006-10-28 14:43 SpeedTouch330_firmware_3012.zip
**-rw-rw-rw- 1 matt matt 776512 2004-03-05 12:03 ZZZL_3.012**

```

I also tried getting rid of "KQD6_3.012", and modem_run, in case they were somehow causing confusion. I then also tried "sudo ./firmware-extractor ZZZL_3.012" in case that helped, but it didn't. 

You're probably thinking that I have just typo'd on the command on something (I know I would be thinking that!), but I know thats  not the problem because the TAB-completion in BASH picked up teh firmware-extractor, and ZZZL_3.012.

Could the problem be that the FE is not working, and for some reason giving that misleading message?

---

### Post by Feline on 2006-10-29
yes...it's the same, identic problem.

I report what ubuntu say to me.

```

yuri@yuri-desktop:~$ unzip SpeedTouch330_firmware_3012.zip 
Archive:  SpeedTouch330_firmware_3012.zip
  inflating: KQD6_3.012              
  inflating: ZZZL_3.012              
[COLOR="Blue"]yuri@yuri-desktop:~$ chmod +x -v firmware-extractor 
mode of `firmware-extractor' retained as 0711 (rwx--x--x)[/COLOR]
yuri@yuri-desktop:~$ ./firmware-extractor KQD6_3.012 
bash: ./firmware-extractor: No such file or directory
yuri@yuri-desktop:~$ ls -l
total 2288
drwxr-xr-x 2 yuri yuri   4096 2006-10-29 21:38 Desktop
lrwxrwxrwx 1 yuri yuri     26 2006-10-28 23:05 Examples -> /usr/share/example-content
[COLOR="Red"]-rwx--x--x 1 yuri yuri  11901 2006-10-29 02:31 firmware-extractor[/COLOR]
-rw-rw-rw- 1 yuri yuri 763677 2004-03-05 12:03 KQD6_3.012
-rw------- 1 yuri yuri      0 2006-10-29 21:19 log.txt~
-rwx------ 1 yuri yuri 769125 2006-10-29 14:53 SpeedTouch330_firmware_3012.zip
-rw-rw-rw- 1 yuri yuri 776512 2004-03-05 12:03 ZZZL_3.012
yuri@yuri-desktop:~$ 



```

in blue i report the script "chmod". you can se that FE exist. chmod work fine and i use "-v" option to print the chand applicated by this script.
in red you can se the list of file in directori /home. firmware-extractor exist.
i try to do all command in sudo mode too. but it work in the same way ç_ç -

i don't know how can i do...

again sorry for my english. i hope my word looks clear ^^

---

### Post by Dr_Freemanstein on 2006-10-30
Same problem here!!

Previously ran 6.06 LTS and aside from the annoying warnings at boot, the connection worked fine.

I try following the same instructions in 6.10 and I get the same as you guys:

> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

mathew@ubuntu:~$ mkdir speedtouch
mathew@ubuntu:~$ 
mathew@ubuntu:~$ mv SpeedTouch330_firmware_3012.zip speedtouch
mathew@ubuntu:~$ 
mathew@ubuntu:~$ cd speedtouch
mathew@ubuntu:~/speedtouch$ 
mathew@ubuntu:~/speedtouch$ unzip SpeedTouch330_firmware_3012.zip
Archive:  SpeedTouch330_firmware_3012.zip
  inflating: KQD6_3.012              
  inflating: ZZZL_3.012              
mathew@ubuntu:~/speedtouch$ cd
mathew@ubuntu:~$ mv firmware-extractor speedtouch
mathew@ubuntu:~$ cd speedtouch &&
> chmod +x firmware-extractor &&
[B][COLOR="Red"]> ./firmware-extractor ZZZL_3.012
bash: ./firmware-extractor: No such file or directory[/COLOR][/B]
mathew@ubuntu:~/speedtouch$ 
mathew@ubuntu:~/speedtouch$ 


Could there be a conflict with the Firmware-Extractor and Edgy??
I assumed this at first, but having seen that some of you have it working is quite puzzling!  The only other option I can think of is to try the source and compile it myself using gcc.  After all, there may be a problem with the precompiled binary??

Just to confirm with everyone, when you click the link to get the precompiled binary, you get a page full of mess right?? Then you save it (saves by default as text file) then rename it from firmware-extractor.txt to just firmware-extractor? Am I doing that bit right??

---

### Post by mwob on 2006-10-30
Fishpie? Anyone?

Someone help me and Feline, please!

---

### Post by mwob on 2006-10-30
Hi Dr_Freemanstein,

I didn't have the same issue as you for getting the pre-compiled firmware-extractor. In firefox in XP, I right-clicked the file, and chose "save as", and it saved it as "firmware-extractor" without me needing to rename it or anything. 

I might try getting it again, to see if that helps. Weird!

---

### Post by MattJ100 on 2006-10-30
I downloaded firmware-extracter from Windows, and installed my speedtouch under Dapper several times with no problem. I kept the extracted firmware files, so I haven't needed to run it again for installing in Edgy.

I just tested running ./firmware-extractor, and strangely, it works fine here.

matthew@matthew-desktop:~/Installers/speedtouch_homecall$ stat firmware-extractor 
  File: `firmware-extractor'
  Size: 11901           Blocks: 24         IO Block: 4096   regular file
Device: 347h/839d       Inode: 278776      Links: 1
Access: (0700/-rwx------)  Uid: ( 1000/ matthew)   Gid: ( 1000/ matthew)
Access: 2006-10-30 09:43:10.000000000 +0000
Modify: 2006-09-14 10:49:18.000000000 +0100
Change: 2006-10-26 16:59:59.000000000 +0100

---

### Post by Dr_Freemanstein on 2006-10-30
> **mwob said:**
> Hi Dr_Freemanstein,

I didn't have the same issue as you for getting the pre-compiled firmware-extractor. In firefox in XP, I right-clicked the file, and chose "save as", and it saved it as "firmware-extractor" without me needing to rename it or anything. 

I might try getting it again, to see if that helps. Weird!

Tried your suggestion, got myself firefox, saved is just as "firmware-extractor" and tried again but still get the very same problem!  This is really strange!  Can anyone shed ANY light on this problem??  Until I get this sorted, I'm stuck with sucky old XP to get online!!  Not only that, but to prevent conflicts, I have to disconnect and reconnect hard-drives between each OS boot!  It's getting annoying, if I could just connect to the net in Ubuntu, I would'nt need XP anymore!

Edit:
Just had a thought...there must be a common factor between those of us who are having this problem (other than the problem! LOL!)

My rig is as follows:
AMD Athlon 64 3200+ Venice
Asus A8N-SLI SE Motherboard
1024Mb DDR 2700 RAM
250Gb Samsung SATA HD
XFX 7300GT 512Mb Graphics
On-board sound
Speedtouch 330 ADSL USB Modem (Silver One)

Installed Ubuntu 6.10 AMD64 on its own on the SATA from alternate cd burned from iso downloaded as torrent (No hash problems).
ALways use alternate disks now, as normal "live" disks cause nothing but havok for me (optical mouse issues!)

---

### Post by MattJ100 on 2006-10-30
```

$ md5sum ./firmware-extractor 
5376cda54b992c35b18ae0d00ab3149f  ./firmware-extractor

```

Is this the same version everyone has? If not, I uploaded the version I downloaded (works fine for me) here: [http://fredj.homecall.co.uk/upload/firmware-extractor](http://fredj.homecall.co.uk/upload/firmware-extractor)

---

### Post by Dr_Freemanstein on 2006-10-30
> **MattJ100 said:**
> ```

$ md5sum ./firmware-extractor 
5376cda54b992c35b18ae0d00ab3149f  ./firmware-extractor

```

Is this the same version everyone has? If not, I uploaded the version I downloaded (works fine for me) here: [http://fredj.homecall.co.uk/upload/firmware-extractor](http://fredj.homecall.co.uk/upload/firmware-extractor)

Tried this file and I get the same result...

> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

mathew@ubuntu:~$ mkdir speedtouch
mathew@ubuntu:~$ 
mathew@ubuntu:~$ mv SpeedTouch330_firmware_3012.zip speedtouch
mathew@ubuntu:~$ 
mathew@ubuntu:~$ cd speedtouch
mathew@ubuntu:~/speedtouch$ 
mathew@ubuntu:~/speedtouch$ unzip SpeedTouch330_firmware_3012.zip
Archive:  SpeedTouch330_firmware_3012.zip
  inflating: KQD6_3.012              
  inflating: ZZZL_3.012              
mathew@ubuntu:~/speedtouch$ cd
mathew@ubuntu:~$ mv firmware-extractor speedtouch
mathew@ubuntu:~$ cd speedtouch &&
> chmod +x firmware-extractor &&
> ./firmware-extractor ZZZL_3.012
[COLOR="Red"]**bash: ./firmware-extractor: No such file or directory**[/COLOR]
mathew@ubuntu:~/speedtouch$ cd
mathew@ubuntu:~$ md5sum firmware-extractor
md5sum: firmware-extractor: No such file or directory
mathew@ubuntu:~$ cd speedtouch
[B][COLOR="Red"]mathew@ubuntu:~/speedtouch$ md5sum firmware-extractor
5376cda54b992c35b18ae0d00ab3149f  firmware-extractor[/COLOR][/B]
mathew@ubuntu:~/speedtouch$ 


This is really odd....how can the same file/instructions work for some but not all????

---

### Post by MattJ100 on 2006-10-30
That's just really... strange.

What happens when you run it with sudo? The same?

---

### Post by stefanokan on 2006-10-30
In order to bypass the problem can someone give speedtch-1.bin and speedtch-2.bin ?
Many thanks.

---

### Post by Dr_Freemanstein on 2006-10-30
How do you mean Matt?

sudo ./firmware-extractor ZZZL_3.012???

But yes, Stefanokan...that could be useful as a workaround!

Anyone??

---

### Post by stefanokan on 2006-10-30
yes, if someone with edgy that has the firmware-extractor working can give the two files already extracted. Thanks

---

### Post by Dr_Freemanstein on 2006-10-30
Yes please, but whoever is good enough to do it may have to provide firmware extracted from both packages.  In case anyone has the same problem but older/newer modem?:D

---

### Post by mwob on 2006-10-30
I have a theory:

I think those of us that can't get it to work are using a 64-bit installation of edgy! I'm using an AMD3500 64Bit, and went for the 64-bit install.

Everyone else think this is the problem? As previously suggested could someone perhaps host those 2 files somewhere?

---

### Post by stefanokan on 2006-10-30
Here's a link:
[http://speedtouchconf.sourceforge.net/rev4fw.zip](http://speedtouchconf.sourceforge.net/rev4fw.zip)
i found it contains:
ZZZLP1.eni
ZZZLP2.eni
that could be renamed as:
speedtch-1.bin
speedtch-2.bin

I had no time to test it but should work.

---

### Post by MattJ100 on 2006-10-30
> **Dr_Freemanstein said:**
> How do you mean Matt?

sudo ./firmware-extractor ZZZL_3.012???

But yes, Stefanokan...that could be useful as a workaround!

Anyone??

Yes: sudo ./firmware-extractor

And here are the files mine produced from the **_[COLOR="Red"][SIZE="2"]ZZZL_3.012[/SIZE][/COLOR]_** package:
[http://fredj.homecall.co.uk/upload/speedtch-1.bin](http://fredj.homecall.co.uk/upload/speedtch-1.bin)
[http://fredj.homecall.co.uk/upload/speedtch-2.bin](http://fredj.homecall.co.uk/upload/speedtch-2.bin)

---

### Post by Dr_Freemanstein on 2006-10-30
Well, as I posted before, I am using AMD64!

Anyone else??

---

### Post by Dr_Freemanstein on 2006-10-30
Wow....two come along at once....yay!

Big big thanks to MattJ and Stefanokan!!!

Will try both just to be sure!

But we must still examine the possibility of a fault with AMD64 Edgy.

---

### Post by stefanokan on 2006-10-30
i'm also using an Edgy amd64.

---

### Post by Dr_Freemanstein on 2006-10-30
Ladies and gentlemen....i think we found our problem!

Pehaps the firmware-extractor is one of those things that won't work in a 64-bit distro??

---

### Post by mwob on 2006-10-30
So, I wonder if this problem is specific to the FE, or if there is a bigger problem executing files from 64bit edgy in general!
 :mad:

---

### Post by Dr_Freemanstein on 2006-10-30
There were already issues with such things ion the AMD64 version of Dapper as far as I know.  I would have thought a great number of those issues would have been fixed for Edgy, but apparantly some persist.  You still have to use workarounds to get some 32-bit apps to work under it.

But as for general execution of files...I don't know yet as the internet connection is the first thing I have tackled so far (can't do much else without it!!)

Edit:
Done it!!  I am now connected thru Ubuntu!  Big big big thanks to MattJ!!

Will say one thing though...had to make a slight change to the standard procedure for Edgy 64:

If you follow this guide [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch) . You will come to a command:

> sudo cp speedtch* /lib/firmware/2.6.15-19-386

this needed to be changed to:

> sudo cp speedtch* /lib/firmware/2.6.17-10-generic

to work in Edgy AMD64.

Other than that...all good.  Now I just have to set everything else up! :D 

Thanks again!:D :D

---

### Post by MattJ100 on 2006-10-30
Great! Glad it works :)

---

### Post by jfrancis on 2006-11-07
Wow.. I have the same issue running the 64bit version of edgy,  but I need the Revision 2 file extracted - KQD6_3.012 - where as the kind people here I believe have done the other file type.

Can anyone either split the KQD6_3.012 file and let me download it, or show me a different program to split the file in a 64bit version of edgy?

Many thanks

---

### Post by MattJ100 on 2006-11-08
[http://getjabber.no-ip.info/modem/](http://getjabber.no-ip.info/modem/)

These are the KQD6_3.012 firmware files only! :)

I'm hoping the fact that I'm not running 64-bit myself makes no difference...

---

### Post by jfrancis on 2006-11-08
I could kiss you!!!! lol :p 

WooHoo!!!  Thank you very much Matt - I am replying to you now from ubuntu :D 

To be honest I was very surprised it worked.. seems so a little bodged but man I am one happy puppy. 

Cheers ears

---

### Post by MattJ100 on 2006-11-08
Wow, glad to hear it worked :D

Happy Ubuntu :)

---

### Post by scaley on 2006-11-09
Thankyou very much for those bin files Matt. and cheers francis for directing me here. Great to find a forum where newbies are treated like real people! lol

---

### Post by scaley on 2006-11-09
OK im still not getting through this.

finally got the bin files in the right place after figuring out how to log on as root (wasnt easy for me)

The next part secrets is tripping me up too.

after creating the file with 
my 'username' * 'password' .
it then tells me to save it as secrets. do i just save to desktop? as after i do, the commands

sudo install -m 600 secrets /etc/ppp/chap-secrets &&
sudo install -m 600 secrets /etc/ppp/pap-secrets

dont work.... 

any ideas?

edit - if i was to just copy and paste my username and password file into the chap secrets and pap secrets files, do i delete the text already there. coz there is no obvious place to add it in.

---

### Post by jfrancis on 2006-11-10
Hi Scaley,

This will be funny. I am a total linux noob giving help :D 

So.. the secrets file.  Grab your login information for your isp.  You need your username (probably in format: [email]name@isp.co.uk[/email] or simular). And also grab your password. Put this in the secrets file.

E.g  In the guide you are following, it has something like:

'USERNAME' * 'PASSWORD'

So you replace the above with your details.  So it follows the format like this:

'name@isk.co.uk' * 'mypassword'

As to where you save it... as long as when you are in terminal you are in the same directory, it should not matter.  Just run the command (the sudo install -m...) and that will copy the file to where it needs to be.  

I found that typing 'ls' in terminal will list the files in the directory I am currently in.  So you can check if the secrets file is there or not first... 

Good luck and let us know how you get on :cool:

---

### Post by scaley on 2006-11-10
OK now firgured out how to use the terminal lol.

Right, i now have the secrets file and the dial files in the right place. Also created the bootscripts fine.

One problem i still have is with the .bin files. I def have the right ones as the little diagnostic thing told me my modem is type 4. eg i need the bin files from the ZZZL file.

The command i have here is. 
sudo cp speedtch* /lib/firmware/2.6.15-19-386

It doesn work, and a quick check tells me i have no folder in lib/firmware called 2.6.15-19-386

only one called 2.6.17-10-generic

I then just dragged and dropped the bin files into this folder (which has loads of bin files already in it)

I guess its not working coz i didnt need to do the first part by making the speedtouch folder. So where do i make this folder, and do i just pop the bin files in it?

---

### Post by scaley on 2006-11-10
OK i just made the folder and put the files in. Im still not online. Double checked the dial files and bootlog are correct and in the right place.

Everytime i try to connect to a website, i get a couple k sent and a couple k received. This makes me think im nearly there. 

Any ideas?

---

### Post by jfrancis on 2006-11-10
Ah.. that is something I ran in to as well ](*,) 

Just copy the file(s) to 2.6.17-10-generic instead.  I read on another thread about this problem, and it worked for me.  

As for your speedtouch folder, as far as I know you don't need that folder once you get it working - it is only a temp location for you to work from.  Don't quote me on that though :-?

---

### Post by scaley on 2006-11-10
Ah nice one. OK so I have done everything. And still no connection. 

Created the dial file 5 or 6 times to check. Same with the bootscript. All the commands are working. Firmware in the right place. Both green lights are on on the modem. Its definately online, as im using the same modem now on a different tower. 

Why wont it work!?!?

---

