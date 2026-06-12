---
title: "Stuck Installing F-Prot Anti-Virus"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by crwenger on 2011-04-11
Hi,

I have managed to download and unpack to the desktop a folder containing F-Prot  AV and can't seem to do anything else with it.  I need a walkthrough as I am a total newbie to ubuntu.

The readme file states "To install, copy this folder to where you wish the install to be located
(for example /opt/f-prot) and run the 'install-f-prot.pl'." but I can't seem to copy it into the folder?  Any help would be greatly appreciated.

---

### Post by Nickjpost on 2011-04-11
> **crwenger said:**
> Hi,

I have managed to download and unpack to the desktop a folder containing F-Prot  AV and can't seem to do anything else with it.  I need a walkthrough as I am a total newbie to ubuntu.

The readme file states "To install, copy this folder to where you wish the install to be located
(for example /opt/f-prot) and run the 'install-f-prot.pl'." but I can't seem to copy it into the folder?  Any help would be greatly appreciated.
  What did you plan to use the antivirus for? Viruses are more of a Windows issue...

---

### Post by samstreet101 on 2011-04-11
Not familiar with F-Prot myself, first question's first; are you adamant you need anti virus? are you new to just Ubuntu or linux in general?

---

### Post by Frogs Hair on 2011-04-11
If you need anti-virus  software for scanning things that may be sent to Windows users use it . If your email provider scans your mail I would not worry.
 
I have never seen this software on any top ten anti-virus list , but that doesn't make is a bad product . 
 
It appears from the site that this is a free trial and then the user has to pay . Avast , AVG, and Clam offer free products for Linux. Avast offers a .deb package , which is much easier to install .
 
You may have to use ```
gksudo nuatilus
``` in order to copy this to a folder if you choose to use this product.

---

### Post by samstreet101 on 2011-04-11
Agreed, if you can find one with a .deb package or an apt you'll have a much easier time installing it

---

### Post by Enigmapond on 2011-04-11
> **Nickjpost said:**
> What did you plan to use the antivirus for? Viruses are more of a Windows issue...

Agreed. You really don't need any anti-virus if you are just using Ubuntu. If you are running a server or have a shared windows drive and really feel the need, just install clamav & clamtk. But again, in 7 years with Linux, I have NEVER needed that kind of protection.

Good Luck!

---

### Post by Dutch70 on 2011-04-11
3 years...no anti-virus, no problems. If windows can't save itself, then...well, you know. :P

I should have said "no virus problems" and...
"no anti-virus problems" lol.

As far as windows though, I really like Avast. I would expect it to be good for Linux also.

---

### Post by crispy_420 on 2011-04-11
So not a single person tries to answer.

You want it in the suggested directory? 'sudo mv f-prot/ /opt'

That should move the f-prot folder to the suggested destination. Then adjust permissions and run script.

---

### Post by crwenger on 2011-04-11
Thanks, for replying to my post.  As I said I am an absolute newbie.  I have no idea on how to open a command console (if one exists) or adjust permissions.  At this point all I have managed to do is install the product the latest version of ubuntu and login to the graphical shell.  I really am looking for a step-by-step walkthrough if I can get one.


> **crispy_420 said:**
> So not a single person tries to answer.

You want it in the suggested directory? 'sudo mv f-prot/ /opt'

That should move the f-prot folder to the suggested destination. Then adjust permissions and run script.

---

### Post by Dutch70 on 2011-04-11
The "command console" in Ubuntu is called Terminal... Menu to Applications >> Accessories >> Terminal. 

Most things can be done with a GUI, but giving directions on a forum is much easier if you use the terminal.

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=623665[/COLOR]]("http://ubuntuforums.org/showthread.php?t=623665")

Not sure if you're using 64-bit or not, but that's what I found via google.

---

### Post by Frogs Hair on 2011-04-11
Here is some documentation and an instruction . The instruction is three years old and I don't know if it is still valid .[http://linuxpoison.blogspot.com/2008/02/howto-useinstall-f-prot-antivirus-on.html](http://linuxpoison.blogspot.com/2008/02/howto-useinstall-f-prot-antivirus-on.html)

[https://help.ubuntu.com/community/XFProt](https://help.ubuntu.com/community/XFProt)

---

### Post by crwenger on 2011-04-11
Thanks.  I've got the terminal up, would you happen to know how to move/copy a folder from the desktop to a target folder?  Will I have to over come access rights?  Thanks.

> **Dutch70 said:**
> The "command console" in Ubuntu is called Terminal... Menu to Applications >> Accessories >> Terminal. 

Most things can be done with a GUI, but giving directions on a forum is much easier if you use the terminal.

[[COLOR=Red]http://ubuntuforums.org/showthread.php?t=623665[/COLOR]]("http://ubuntuforums.org/showthread.php?t=623665")

Not sure if you're using 64-bit or not, but that's what I found via google.

---

### Post by crwenger on 2011-04-11
I don't think that is much relative F-Prot appears to be only release as a Tar-Zip archive?

> **Frogs Hair said:**
> Here is some documentation and an instruction . The instruction is two years old and I don't know if it is still valid .[http://linuxpoison.blogspot.com/2008/02/howto-useinstall-f-prot-antivirus-on.html](http://linuxpoison.blogspot.com/2008/02/howto-useinstall-f-prot-antivirus-on.html)

[https://help.ubuntu.com/community/XFProt](https://help.ubuntu.com/community/XFProt)

---

### Post by crwenger on 2011-04-11
It doesn't look like F-Prot has released a .deb package of it's AV package.

> **Dutch70 said:**
> The "command console" in Ubuntu is called Terminal... Menu to Applications >> Accessories >> Terminal. 

Most things can be done with a GUI, but giving directions on a forum is much easier if you use the terminal.

[[COLOR=Red]http://ubuntuforums.org/showthread.php?t=623665[/COLOR]]("http://ubuntuforums.org/showthread.php?t=623665")

Not sure if you're using 64-bit or not, but that's what I found via google.

---

### Post by Frogs Hair on 2011-04-11
> **crwenger said:**
> I don't think that is much relative F-Prot appears to be only release as a Tar-Zip archive?

Yes , your right , I just checked at the site  and they have changed the package type . That instruction was the only one for Ubuntu that I have been able to find so far . Welcome to the forums , I forgot that earlier .

Hopefully someone who has installed that software recently will see your thread . If  you feel the need to use anti-virus software , go for it , I used Clam when I first installed Ubuntu , but it only checks for Windows viruses and I wasn't sending attachments that I had to worry about.

---

### Post by crwenger on 2011-04-11
As some following the thread may have guessed I am hoping to use ubuntu to validate scan results for a Microsoft environment; F-Prot has provided installation instructions but I just don't have the background to make much sense of the readme.  Even my attempts to copy/move the AV folder from the desktop using the File Browser have failed?


> **Frogs Hair said:**
> Yes , your right , I just checked at the site  and they have changed the package type . That instruction was the only one for Ubuntu that I have been able to find so far . Welcome to the forums , I forgot that earlier .

Hopefully someone who has installed that software recently will see your thread . If  you feel the need to use anti-virus software , go for it , I used Clam when I first installed Ubuntu , but it only checks for Windows viruses and I wasn't sending attachments that I had to worry about.

---

### Post by Dutch70 on 2011-04-11
> **crwenger said:**
> Thanks.  I've got the terminal up, would you happen to know how to move/copy a folder from the desktop to a target folder?  Will I have to over come access rights?  Thanks.

lol, no I don't, but you can cut/paste it to the folder just like in windows if you know where the target folder is.

Mind if I ask why exactly you want an anti-virus?

---

### Post by crwenger on 2011-04-11
I tried copy and pasting the F-Prot folder using the explorer but when I go to 'paste' it is greyed out?

SRC:  /home/crwenger/Desktop/

TRG: /opt

> **Dutch70 said:**
> lol, no I don't, but you can cut/paste it to the folder just like in windows if you know where the target folder is.

Mind if I ask why exactly you want an anti-virus?

---

### Post by Frogs Hair on 2011-04-11
See post #4 on this thread , there are different ways to install a tar .gz and that is why it is difficult to find one method that applies to every file.  The read me page   sometimes gives detailed instructions on how to install a particular package and sometimes it only  advises as to where to move the file .[http://ubuntuforums.org/showthread.php?t=246092](http://ubuntuforums.org/showthread.php?t=246092)

---

### Post by crwenger on 2011-04-11
Here is the output from a terminal session and the results:

crwenger@crwenger-ubuntu:~$ cd /usr/local
crwenger@crwenger-ubuntu:/usr/local$ gunzip -c /home/crwenger/Desktop/fp-Linux-i686-ws.tar.gz | tar -xvf -
./f-prot/
tar: ./f-prot: Cannot mkdir: Permission denied
./f-prot/doc/
tar: ./f-prot/doc: Cannot mkdir: No such file or directory
./f-prot/doc/man/
tar: ./f-prot/doc/man: Cannot mkdir: No such file or directory
./f-prot/doc/man/f-prot.conf.5
tar: ./f-prot/doc/man/f-prot.conf.5: Cannot open: No such file or directory
./f-prot/doc/man/fpscan.1
tar: ./f-prot/doc/man/fpscan.1: Cannot open: No such file or directory
./f-prot/doc/man/fpupdate.8
tar: ./f-prot/doc/man/fpupdate.8: Cannot open: No such file or directory
./f-prot/doc/html/
tar: ./f-prot/doc/html: Cannot mkdir: No such file or directory
./f-prot/doc/html/Helpfiles_v6/
tar: ./f-prot/doc/html/Helpfiles_v6: Cannot mkdir: No such file or directory
./f-prot/doc/html/Helpfiles_v6/mailscanner.html
tar: ./f-prot/doc/html/Helpfiles_v6/mailscanner.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/sys_req.html
tar: ./f-prot/doc/html/Helpfiles_v6/sys_req.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/inst_pro.html
tar: ./f-prot/doc/html/Helpfiles_v6/inst_pro.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/fpscand_conf.html
tar: ./f-prot/doc/html/Helpfiles_v6/fpscand_conf.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/prot_samba.html
tar: ./f-prot/doc/html/Helpfiles_v6/prot_samba.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/fpscan.html
tar: ./f-prot/doc/html/Helpfiles_v6/fpscan.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/main_feat.html
tar: ./f-prot/doc/html/Helpfiles_v6/main_feat.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/fpmon_options.html
tar: ./f-prot/doc/html/Helpfiles_v6/fpmon_options.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/fpscan_options.html
tar: ./f-prot/doc/html/Helpfiles_v6/fpscan_options.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/updater.html
tar: ./f-prot/doc/html/Helpfiles_v6/updater.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/qmail_scan.html
tar: ./f-prot/doc/html/Helpfiles_v6/qmail_scan.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/loglevel.html
tar: ./f-prot/doc/html/Helpfiles_v6/loglevel.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/test_eicar.html
tar: ./f-prot/doc/html/Helpfiles_v6/test_eicar.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/index.html
tar: ./f-prot/doc/html/Helpfiles_v6/index.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/auto_updt.html
tar: ./f-prot/doc/html/Helpfiles_v6/auto_updt.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/appendix_a.html
tar: ./f-prot/doc/html/Helpfiles_v6/appendix_a.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/add_info.html
tar: ./f-prot/doc/html/Helpfiles_v6/add_info.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/appendix_b.html
tar: ./f-prot/doc/html/Helpfiles_v6/appendix_b.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/fpscand_options.html
tar: ./f-prot/doc/html/Helpfiles_v6/fpscand_options.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/man_updt.html
tar: ./f-prot/doc/html/Helpfiles_v6/man_updt.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/appendix_c.html
tar: ./f-prot/doc/html/Helpfiles_v6/appendix_c.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/milter_scan.html
tar: ./f-prot/doc/html/Helpfiles_v6/milter_scan.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/images/
tar: ./f-prot/doc/html/Helpfiles_v6/images: Cannot mkdir: No such file or directory
./f-prot/doc/html/Helpfiles_v6/images/test_eicar.gif
tar: ./f-prot/doc/html/Helpfiles_v6/images/test_eicar.gif: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/images/arrow_right.gif
tar: ./f-prot/doc/html/Helpfiles_v6/images/arrow_right.gif: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/images/dazuko.gif
tar: ./f-prot/doc/html/Helpfiles_v6/images/dazuko.gif: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/images/banner.gif
tar: ./f-prot/doc/html/Helpfiles_v6/images/banner.gif: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/images/arrow_left.gif
tar: ./f-prot/doc/html/Helpfiles_v6/images/arrow_left.gif: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/images/using_fprot_so_v6.gif
tar: ./f-prot/doc/html/Helpfiles_v6/images/using_fprot_so_v6.gif: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/images/notusing_fprot_so_v6.gif
tar: ./f-prot/doc/html/Helpfiles_v6/images/notusing_fprot_so_v6.gif: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/images/fpupdate.gif
tar: ./f-prot/doc/html/Helpfiles_v6/images/fpupdate.gif: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/chmstyle.css
tar: ./f-prot/doc/html/Helpfiles_v6/chmstyle.css: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/fpmon.html
tar: ./f-prot/doc/html/Helpfiles_v6/fpmon.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/todo.txt
tar: ./f-prot/doc/html/Helpfiles_v6/todo.txt: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/fprots.html
tar: ./f-prot/doc/html/Helpfiles_v6/fprots.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/loc_files.html
tar: ./f-prot/doc/html/Helpfiles_v6/loc_files.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/fpupdate_options.html
tar: ./f-prot/doc/html/Helpfiles_v6/fpupdate_options.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/fpmon_conf.html
tar: ./f-prot/doc/html/Helpfiles_v6/fpmon_conf.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/test_inst.html
tar: ./f-prot/doc/html/Helpfiles_v6/test_inst.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/fpscand.html
tar: ./f-prot/doc/html/Helpfiles_v6/fpscand.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/per_scan.html
tar: ./f-prot/doc/html/Helpfiles_v6/per_scan.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/scan_with_mailscanner.html
tar: ./f-prot/doc/html/Helpfiles_v6/scan_with_mailscanner.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/conf_scanmail_bootup.html
tar: ./f-prot/doc/html/Helpfiles_v6/conf_scanmail_bootup.html: Cannot open: No such file or directory
./f-prot/doc/html/Helpfiles_v6/postfix_scan.html
tar: ./f-prot/doc/html/Helpfiles_v6/postfix_scan.html: Cannot open: No such file or directory
./f-prot/doc/LICENSE
tar: ./f-prot/doc/LICENSE: Cannot open: No such file or directory
./f-prot/doc/LICENSES-others
tar: ./f-prot/doc/LICENSES-others: Cannot open: No such file or directory
./f-prot/doc/LICENSE-FPAV
tar: ./f-prot/doc/LICENSE-FPAV: Cannot open: No such file or directory
./f-prot/doc/CHANGES
tar: ./f-prot/doc/CHANGES: Cannot open: No such file or directory
./f-prot/install-f-prot.pl
tar: ./f-prot/install-f-prot.pl: Cannot open: No such file or directory
./f-prot/product.data
tar: ./f-prot/product.data: Cannot create symlink to `product.data.default': No such file or directory
./f-prot/antivir.def
tar: ./f-prot/antivir.def: Cannot open: No such file or directory
./f-prot/README
tar: ./f-prot/README: Cannot open: No such file or directory
./f-prot/product.data.default
tar: ./f-prot/product.data.default: Cannot open: No such file or directory
./f-prot/fpscan
tar: ./f-prot/fpscan: Cannot open: No such file or directory
./f-prot/fpupdate
tar: ./f-prot/fpupdate: Cannot open: No such file or directory
./f-prot/f-prot.conf.default
tar: ./f-prot/f-prot.conf.default: Cannot open: No such file or directory
./f-prot/license.key
tar: ./f-prot/license.key: Cannot open: No such file or directory
tar: Exiting with failure status due to previous errors
crwenger@crwenger-ubuntu:/usr/local$ 

Any ideas why it failed?

> **crispy_420 said:**
> So not a single person tries to answer.

You want it in the suggested directory? 'sudo mv f-prot/ /opt'

That should move the f-prot folder to the suggested destination. Then adjust permissions and run script.

---

### Post by crispy_420 on 2011-04-12
For starters you are running as a normal user with no admin rights. Also you are looking to unpack from wrong directory. Try what I mentioned before and keep it simple since the commandline (terminal) is new to you. 

Just right click the downloaded file (.tar?) and select extract. You then have a new folder created called f-prot right. 

Looks like you are doing this from your desktop right? So in that case we are going to navigate to Desktop folder in terminal. Open the terminal under Accessories Menu and navigate to the desktop via:
cd /home/crwenger/Desktop

Now we verify folder is there and still keeping it simple from the terminal:
ls

The f-prot folder should be listed right? If not you are in the wrong directory. Next we will move that folder to the /opt directory via what I first mentioned but we will do so with root(sudo) rights:
sudo mv f-prot/ /opt

Check the /opt folder in GUI. Is the f-prot folder now there? Now we will navigate over there to run the scripts to install and also change permissions too so:
cd /opt
& 
ls 
F-prot folder should be present right? Now to change permissions for the folder to root control and allow executing if not already done so:
chmod -R 0755

Now navigate into that folder are follow the read me file from there:
cd f-prot/

Any help?

---

### Post by crwenger on 2011-04-12
Following your instructions I was able to move the F-Prot folder to the /opt folder.  However when I try to run the command to change folder permissions I get the following error:

crwenger@crwenger-ubuntu:~$ cd /opt
crwenger@crwenger-ubuntu:/opt$ ls
f-prot
crwenger@crwenger-ubuntu:/opt$ chmod -R 0755
chmod: missing operand after `0755'
Try `chmod --help' for more information.
crwenger@crwenger-ubuntu:/opt$ 



> **crispy_420 said:**
> For starters you are running as a normal user with no admin rights. Also you are looking to unpack from wrong directory. Try what I mentioned before and keep it simple since the commandline (terminal) is new to you. 

Just right click the downloaded file (.tar?) and select extract. You then have a new folder created called f-prot right. 

Looks like you are doing this from your desktop right? So in that case we are going to navigate to Desktop folder in terminal. Open the terminal under Accessories Menu and navigate to the desktop via:
cd /home/crwenger/Desktop

Now we verify folder is there and still keeping it simple from the terminal:
ls

The f-prot folder should be listed right? If not you are in the wrong directory. Next we will move that folder to the /opt directory via what I first mentioned but we will do so with root(sudo) rights:
sudo mv f-prot/ /opt

Check the /opt folder in GUI. Is the f-prot folder now there? Now we will navigate over there to run the scripts to install and also change permissions too so:
cd /opt
& 
ls 
F-prot folder should be present right? Now to change permissions for the folder to root control and allow executing if not already done so:
chmod -R 0755

Now navigate into that folder are follow the read me file from there:
cd f-prot/

Any help?

---

### Post by Dutch70 on 2011-04-12
I believe you need to put the name of the file/folder after that command.
```
chmod -R 0755 f-prot
```

If that doesn't help, you can right click the folder & select properties and either click "Help" on the bottom left. or click the permissions tab.

---

### Post by crispy_420 on 2011-04-12
Dutch is correct. In my rush I forgot that detail and mentioning sudo:

sudo chmod -R 0755 f-prot/

Sorry.

---

### Post by crwenger on 2011-04-12
I tried executing the script and it returned:

crwenger@crwenger-ubuntu:~$ cd /opt
crwenger@crwenger-ubuntu:/opt$ ls
f-prot
crwenger@crwenger-ubuntu:/opt$ chmod -R 0755
chmod: missing operand after `0755'
Try `chmod --help' for more information.
crwenger@crwenger-ubuntu:/opt$ chmod -R 0755 f-prot
crwenger@crwenger-ubuntu:/opt$ cd f-prot
crwenger@crwenger-ubuntu:/opt/f-prot$ ls
antivir.def  f-prot.conf.default  install-f-prot.pl  product.data.default
doc          fpscan               license.key        README
f-prot.conf  fpupdate             product.data
crwenger@crwenger-ubuntu:/opt/f-prot$ install-f-prot.pl
install-f-prot.pl: command not found
crwenger@crwenger-ubuntu:/opt/f-prot$ ./install-f-prot.pl


    (c) FRISK Software International

    [http://www.f-prot.com/](http://www.f-prot.com/)

    You are about to install F-Prot Antivirus for Linux Workstations
     on a Debian Linux 2.6.32 running on i686 into the '/opt/f-prot'
    directory

/opt/f-prot/f-prot.conf already exists, not copying /opt/f-prot/f-prot.conf.default to that location


 Failed to create symbolic link '/etc/f-prot.conf -> /opt/f-prot/f-prot.conf': Permission denied 

 Fix the above errors and then re-run this script or install manually

crwenger@crwenger-ubuntu:/opt/f-prot$

---

### Post by crispy_420 on 2011-04-12
Again not running as an admin user will cause this. Try:

sudo ./install-f-prot.pl

---

### Post by crwenger on 2011-04-12
Here is the final output:

crwenger@crwenger-ubuntu:~$ cd /opt
crwenger@crwenger-ubuntu:/opt$ ls
f-prot
crwenger@crwenger-ubuntu:/opt$ chmod -R 0755
chmod: missing operand after `0755'
Try `chmod --help' for more information.
crwenger@crwenger-ubuntu:/opt$ chmod -R 0755 f-prot
crwenger@crwenger-ubuntu:/opt$ cd f-prot
crwenger@crwenger-ubuntu:/opt/f-prot$ ls
antivir.def  f-prot.conf.default  install-f-prot.pl  product.data.default
doc          fpscan               license.key        README
f-prot.conf  fpupdate             product.data
crwenger@crwenger-ubuntu:/opt/f-prot$ install-f-prot.pl
install-f-prot.pl: command not found
crwenger@crwenger-ubuntu:/opt/f-prot$ ./install-f-prot.pl


    (c) FRISK Software International

    [http://www.f-prot.com/](http://www.f-prot.com/)

    You are about to install F-Prot Antivirus for Linux Workstations
     on a Debian Linux 2.6.32 running on i686 into the '/opt/f-prot'
    directory

/opt/f-prot/f-prot.conf already exists, not copying /opt/f-prot/f-prot.conf.default to that location


 Failed to create symbolic link '/etc/f-prot.conf -> /opt/f-prot/f-prot.conf': Permission denied 

 Fix the above errors and then re-run this script or install manually

crwenger@crwenger-ubuntu:/opt/f-prot$  sudo ./install-f-prot.pl
[sudo] password for crwenger: 


    (c) FRISK Software International

    [http://www.f-prot.com/](http://www.f-prot.com/)

    You are about to install F-Prot Antivirus for Linux Workstations
     on a Debian Linux 2.6.32 running on i686 into the '/opt/f-prot'
    directory

/opt/f-prot/f-prot.conf already exists, not copying /opt/f-prot/f-prot.conf.default to that location

Where do you want a symbolic link to 'F-Prot Antivirus command line scanner (fpscan)' to be created?
(Just press Enter to accept the default) [/usr/local/bin]: 

Where do you want a symbolic link to 'section 8 manuals' to be created?
(Just press Enter to accept the default) [/usr/local/man/man8]: 

/usr/local/man/man8 doesn't exist. Create it?
(Just press Enter to accept the default) [Y/n]: y

Where do you want a symbolic link to 'section 1 manuals' to be created?
(Just press Enter to accept the default) [/usr/local/man/man1]: 

/usr/local/man/man1 doesn't exist. Create it?
(Just press Enter to accept the default) [Y/n]: y

Where do you want a symbolic link to 'section 5 manuals' to be created?
(Just press Enter to accept the default) [/usr/local/man/man5]: 

/usr/local/man/man5 doesn't exist. Create it?
(Just press Enter to accept the default) [Y/n]: y

Changing file access permissions on the installed files and directories ...ok
Checking if you have an existing license key...yes

Found an existing license key in /opt/f-prot/license.key, updating antivir.def ...

Error: Incorrect checksum of downloaded update
Downloading update (%0)

Unable to update `antvir.def' with the provided license key.
The error message above should explain why.

Continue with installation?
(Just press Enter to accept the default) [Y/n]: y

Installation will now continue, you can try running fpupdate later to update `antivir.def'

We've generated the following crontab entries to update the
antivir.def file via fpupdate. Updates will be run hourly at a
randomly picked minute to distribute load, and thus make your updates
faster than if they were run during obvious high load times, e.g. on
the hour.

The global crontab entry we made to add to /etc/crontab is the following:

    31 * * * * root /opt/f-prot/fpupdate > /dev/null

Would you like to have this crontab appended to /etc/crontab?
(Just press Enter to accept the default) [Y/n]: 


    All done!



If you reconfigured your MTA you should restart it now to activate the changes.

    Have a nice day

Frisk software ([www.f-prot.com](www.f-prot.com))

crwenger@crwenger-ubuntu:/opt/f-prot$ 


> **crispy_420 said:**
> Again not running as an admin user will cause this. Try:

sudo ./install-f-prot.pl

---

### Post by crispy_420 on 2011-04-12
Looks like it worked, right?

---

### Post by crwenger on 2011-04-12
LOL!  Don't know how to tell.  I think the script executed and I have found the command line scanner at the /usr/local/bin folder but I am not certain about anything else.

> **crispy_420 said:**
> Looks like it worked, right?

---

### Post by crispy_420 on 2011-04-12
There is a third party gui for it if you feel more comfortable. Guide may be a bit dated but here is an older howto to get the gui setup:

[http://www.howtoforge.com/f_prot_antivirus_ubuntu_feisty](http://www.howtoforge.com/f_prot_antivirus_ubuntu_feisty)

---

### Post by crispy_420 on 2011-04-12
Did some searching directly for it and here is a direct link to the GUI called xfprot:

[http://web.tiscali.it/sharp/xfprot/xfprot_2.4-1_i386.deb](http://web.tiscali.it/sharp/xfprot/xfprot_2.4-1_i386.deb)

You can read on it here: [http://web.tiscali.it/sharp/xfprot/](http://web.tiscali.it/sharp/xfprot/)

Now you can test it out. You can download a test file through eicar to test functionality here: [http://www.eicar.org/anti_virus_test_file.htm](http://www.eicar.org/anti_virus_test_file.htm)

Think you can setup scheduled scans but not really necessary at the current time unless you are running a windows file share. But you can easy run on demand scans as needed.

---

### Post by crwenger on 2011-04-13
I installed the GUI but I it doesn't seem to add an item to the start menu and I don't know where to launch it from otherwise?

> **crispy_420 said:**
> Did some searching directly for it and here is a direct link to the GUI called xfprot:

[http://web.tiscali.it/sharp/xfprot/xfprot_2.4-1_i386.deb](http://web.tiscali.it/sharp/xfprot/xfprot_2.4-1_i386.deb)

You can read on it here: [http://web.tiscali.it/sharp/xfprot/](http://web.tiscali.it/sharp/xfprot/)

Now you can test it out. You can download a test file through eicar to test functionality here: [http://www.eicar.org/anti_virus_test_file.htm](http://www.eicar.org/anti_virus_test_file.htm)

Think you can setup scheduled scans but not really necessary at the current time unless you are running a windows file share. But you can easy run on demand scans as needed.

---

### Post by jtarin on 2011-04-13
Open a terminal and issue the command ```
sudo xfprot
```as to the menu item sometimes applications will place an entry after reboot.

---

### Post by crispy_420 on 2011-04-14
My post (#30) has a link to add the GUI into the a menu link via a little manual work.

Or xfprot via command line, not sure if sudo is needed.

---

### Post by jtarin on 2011-04-14
> **crispy_420 said:**
> My post (#30) has a link to add the GUI into the a menu link via a little manual work.

Or xfprot via command line, not sure if sudo is needed.Your right...its at the bottom of the page of the link you gave.

---

### Post by crwenger on 2011-04-14
It took a little research but I managed to setup a share and dump a few files for testing our Windows AV solution against F-Prot and generate a report.  I would to thank everyone that helped me in my efforts, I am certain that this will be valuable asset to our corporate network.

> **crispy_420 said:**
> My post (#30) has a link to add the GUI into the a menu link via a little manual work.

Or xfprot via command line, not sure if sudo is needed.

---

### Post by crispy_420 on 2011-04-15
Mark as solved?

---

