---
title: "Rebuilding GRUB on multiboot system"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by msfisher on 2008-12-28
Due to hardware incompatibilities, I've installed and reinstalled several distros.  Recently, those incompatibilities went away when I installed Intrepid to a system with Windows 98, OpenSuse and Mandriva on it.  During the install the installer spotted all three other OS's and set up Grub for them.  When the kernels under OpenSuse and Mandriva were updated, the Grub installed by Intrepid became incorrect -- the vmlinuz vector pointed to a now nonexistent file.  In addition, I just installed the newest OpenSuse which stuck its own Grub in place with only OpenSuse listed (first time it's done that). 

I've searched a lot of forums and online sources, and I cannot find a utility to do what Ubuntu apparently does during its installation -- search all the hard drives for bootable OS's and set up the menu list.  I realize I can do it manually by editing Grub's menu.lst, but I don't always know all the switches to include in the menu entry (I've tried it this way with mixed results -- got one distro right, the other wrong).  I've also tried Super Grub Disk, which is great for reestablishing an existing Grub (I used it to replace the Grub OpenSuse installed with the mostly-working Intrepid one), but seems unable to build a new Grub based on scanning the drives for bootable OS's.  It does scan, and seems relatively accurate (the last time  used it, it reported my Mandriva install as Fedora).  

So my questions:  Since the Ubuntu installer is capable of setting up Grub, is there a way to get at that function  without going through a full installation?  Is there an equivalent to OpenSuse's "repair" which can do it?  Have I overlooked a capability of Super Grub Disk?  Lastly, is there a utility out there that can do it?

---

### Post by northern lights on 2008-12-28
Boot into openSUSE, open any terminal emulator and run```
sudo grub
```Alternatively you could log-in as root in openSUSE and just run```
grub
```
Whatever way you do it you now get a *grub* prompt. Here do```
grub> find /boot/grub/stage1
grub> root (hdX,Y)      \\put X,Y according to the last line's output
grub> setup (hd0)
grub> quit
```
Reboot. You should be set.

---

### Post by balaknair on 2008-12-28
Check these pages

1) With SuperGrubDisk
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk)


2) From the Ubuntu Live CD, using a Grub shell
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

This is basically what Northern Lights has described above


2) From the Ubuntu Live CD, using the GUI
[https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)

---

### Post by bodhi.zazen on 2008-12-28
See if this thread helps as well

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by msfisher on 2008-12-28
First off, thanks for the quick replies.

However, both of them lead to the same spots -- reloading an existing Grub or manually editing the menu.lst.

Perhaps I wasn't clear -- Is there some more or less automated way to build a NEW Grub like Ubuntu's installer does?

---

### Post by balaknair on 2008-12-28
> **msfisher said:**
> First off, thanks for the quick replies.

However, both of them lead to the same spots -- reloading an existing Grub or manually editing the menu.lst.

Perhaps I wasn't clear -- Is there some more or less automated way to build a NEW Grub like Ubuntu's installer does?

Check the material at 
[https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)

I think it explains how to re-install GRUB from the GUI via the partitioner(replicating the install process but not formatting anything). I believe it creates a new GRUB.

---

### Post by northern lights on 2008-12-28
> **balaknair said:**
> Check the material at 
[https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)
This is "the material at [...]":> **above link]Command line

   1. Boot your computer up with Ubuntu CD
   2. Open a terminal window or switch to a tty.
   3.

      Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
   4. Type "grub"
   5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
   6. Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
   7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
   8. Quit grub by typing "quit".
   9. Reboot and remove the bootable CD. [/QUOTE][QUOTE=northern lights said:**
> ```
sudo grub
grub> find /boot/grub/stage1
grub> root (hdX,Y)      \\put X,Y according to the last line's output
grub> setup (hd0)
grub> quit
```
Reboot.
;-)

---

### Post by balaknair on 2008-12-28
@Northern Lights

In [https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)
the section just above what you have quoted is what I wanted to point out

> GUI

   1. Boot your computer up with Ubuntu CD
   2. Go through all the process until you reach "[!!!] Disk Partition"
   3. Select Manual Partition
   4. Mount your appropriate linux partions  / /boot swap ..... 
   5. DO NOT FORMAT THEM.
   6. Finish the manual partition
   7. Say "Yes" when it asks you to save the changes
   8. It will give you errors saying that "the system couldn't install ....." after that
   9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
  10. Jump to "Install Grub ...."
  11. Once it is finished, just restart your computer

:D

---

### Post by louieb on 2008-12-28
> **bodhi.zazen said:**
> ...[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

> **msfisher said:**
> ...However, both of them lead to the same spots -- reloading an existing Grub or manually editing the menu.lst.

Perhaps I wasn't clear -- Is there some more or less automated way to build a NEW Grub like Ubuntu's installer does?

Look closely at bodhi.zazen link. Easy enough to keep grub in sync when there is a kernel update. (easy like you don't do anything). Each distribution keeps it own GRUB configuration and updates only it GRUB files when there is a kernel upgrade.   

Things to look for in the link are **chainload **and **configfile**.

My favorite way is to use a  [dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")  not to be confused with a /boot partition they are two different things.

You'll learn alot about GRUB heres a good place to start. [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by cariboo on 2008-12-28
I personally prefer the configfile method. Sometimes  drive order changes so using the blkid of your partitions gets around that problem. Right now I triple boot Vista, Intrepid and Jaunty. I'm using Jaunty as my main OS so I add Intrepid to grub using uuid and configfile eg:

```
title		Intrepid
uuid		9f702ef1-20bd-4aef-8f22-cd6830d83a50
configfile	/boot/grub/menu.lst
```

This also helps when kernels are updated on different installations.

Jim

---

### Post by msfisher on 2008-12-28
As before, thanks to all for the replies.

The net answer seems to be that yes, there are somewhat automatic ways to keep Grub up to date when there are updates and/or new OS's added (say replacing Fedora with Sabayon).  I'll probably try one or more of the solutions you guys linked to.

However, no, there aren't any separate utilities which scan drives for bootable OS's and pass the information on to menu.lst (what Ubuntu does during installation).

Am I following this right?

OK.  Last question:  How does Ubuntu do it?  I mean, how does it find all the bootable OS's and set up Grub?

---

### Post by balaknair on 2008-12-29
I'm guessing it uses a tool called os-prober which scans each bootable partition for system boot files(bootrec.exe in Vista, boot.ini in XP, symlinks for initrd.img and vmlinuz in Linux). It will also look for other bootloader files(like lilo or a Vista bootloader modded with EasyBCD). These will be visible within the primary partition(not in subfolders on those partitions), so it doesn't have to scan the entire drive.

This is just what I could understand from reading up on this a while ago(while looking for info on Wubi).

---

### Post by msfisher on 2008-12-31
balaknair:  Thanks!  Your guess sounds very good.  I'm sure you did the same thing I did and Googled os-prober and found out its from the Debian installer.  Logical, since Ubuntu is based on Debian.  It's even downloadable from Ubuntu through Jaunty.

My next goal, then, is to read up on os-prober and see if some industrious programmer has worked up a front end -- or at least if I can figure out how to run it from a CD or USB drive.  I'm old enough to have spent my computer-formative years running apps from the command line, but I prefer a GUI.  Lazy, I expect.

Anyway, thanks again.

---

### Post by balaknair on 2009-01-02
I tried searching for a GUI front-end to os-prober, no luck so far. If you do find something, do post a reply(with maybe a link to relevant material). Just curious about stuff like that(though it would be a great utility to have when troubleshooting GRUB errors).

---

### Post by handydan918 on 2009-01-02
I don't know of any program to do what you want, but the Mepis linux distro will. It has the capability of reinstalling grub from the live cd. If that doesn't work, you may have to install it, and that will do it fer sher. I have used Mepis for several years, and have never had it fail to detect an O/S.

---

### Post by balaknair on 2009-01-02
@handydan918
Mepis is again a Debian derivative, and probably uses the same tools(os-prober) as Ubuntu to detect other OS installations.
Ubuntu too can reinstall GRUB, but it's a bit iffy(looks scary)
[https://help.ubuntu.com/community/GrubHowto#GUI](https://help.ubuntu.com/community/GrubHowto#GUI)
It's not something I'd try unless my system was already messed up(and I had nothing to lose).

---

### Post by msfisher on 2009-01-02
Handydan & balaknair:

Along the way I found out that you can reinstall an existing Grub the way it's described.  In fact, that's what I'm running off of right now -- a reinstalled Grub.  What you can't do is re-scan the system for other OS's and/or mount points.  

I started looking into os-prober, and the Ubuntu package information warns heavily against trying to do standalone work with it.  It is "advertised" as being only for installers.

As it happens, I had some sort of freak crash yesterday and only just got up and running again, mainly by using the repair facility in Ubuntu.  So,  once again, a Linux distro (Ubuntu this time) can boot but not recognize other OS's, this time including Windows.  It could find all of them before.  Guess I'll have to reinstall Ubuntu after all.  Drat.

---

### Post by handydan918 on 2009-01-02
> **balaknair said:**
> @handydan918
Mepis is again a Debian derivative, and probably uses the same tools(os-prober) as Ubuntu to detect other OS installations.

Reasonable assumption, but wrong. Mepis has tools that are not gpl'd, so no other O/S has them.
The MEPIS tools (there are several) are more than just front-ends for commandline stuff. Mepis has been reinstalling grub from a live cd since before Ubu  was an itch in Shuttleworth's imagination.

---

### Post by northern lights on 2009-01-02
> **handydan918 said:**
> I don't know of any program to do what you want, but the Mepis linux distro will.
+1 for trying to let Mepis work it's magic.

> **balaknair said:**
> @Northern Lights
In [https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)> GUI

1. Boot your computer up with Ubuntu CD
2. Go through all the process until you reach "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions / /boot swap .....
5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer
the section just above what you have quoted is what I wanted to point out.

> **handydan918 said:**
> [...] just front-ends for commandline stuff [...]

Man, balaknair, the "GUI" sections is the _exact same_ thing as the "commandline" section that follows it. Mere difference: you can click your way through.

---

### Post by balaknair on 2009-01-03
@handydan918:

OK. :D
I haven't used MEPIS much- just once, couple of years back when it wouldn't detect my hard drive(neither would Ubuntu Dapper or any other distro)- so I don't know much about it. As you noted, it was just an assumption based on MEPIS' Debian origins. Maybe I'll download the iso and give it a spin(the latest version is in RC1, when it's RTM perhaps).
Thanks for the info.

@northern lights:
I think I know what you mean. What I was trying to point out was in response to msfisher's question about 'installing' GRUB preferably via the GUI(emphasis on the GUI, 'cos us noobs still prefer to 'click our way through'). Though now I'm a bit confused about the whole issue.
I just thought that since the guide says 'install GRUB' and during the Ubuntu install process the installer scans the drive for other OSes, it would actually build and install a new GRUB.
And 2 more doubts- 
1) in the GRUB shell, will 'find /boot/grub/stage1' scan the drive for other OSes or will it scan the drive for an existing GRUB?
2) does the GUI installer, as used in the guide I referred to, scan the drive for other OSes or does it just find an existing GRUB(I'm still confused though, couldn't those GUI steps build a new GRUB, since the partitioner scans the drives?)?

---

### Post by northern lights on 2009-01-03
> **balaknair said:**
> in the GRUB shell, will 'find /boot/grub/stage1' scan the drive for other OSes or will it scan the drive for an existing GRUB?
The *find* command searches for existing files. Searching for */boot/grub/stage1* helps determine the device which should be set as root via the *root (hdX,Y)* command.
The command *setup (hd0)* writes a new GRUB to the first drive's MBR.

In the GUI approach (which undoubtedly could be easier for the inexperienced user that is not familiar with a CLI at all), step 4 (Mount your appropriate linux partions / /boot swap .....) essentially replaces the *find /boot/grub/stage1* command, as mounting "/" is finding "root". Step 10 (Jump to "Install Grub ....") is *setup (hd0)*. The GUI executes these exact shell commands in the background.

> **balaknair said:**
> Does the GUI installer, as used in the guide I referred to, scan the drive for other OSes or does it just find an existing GRUB(I'm still confused though, couldn't those GUI steps build a new GRUB, since the partitioner scans the drives?)?
Unfortunately in the partitioner step(s), the drives are not scanned, as you manually mount /. Swap is negligible and /boot you will usually not manually mount, because there's no separate /boot partition in the standard Ubuntu install.

The GRUB setup just writes GRUB to the MBR. As you know from experience, the menu.lst does not reside in the MBR, but in /boot/grub/ on the Ubuntu partition. It is not written by GRUB, but by the Ubuntu installer, which is unfortunately not being run in the above GUI procedure (see steps 8 & 9).

If you were to figure which tool does this and how to run it correctly outside the installer, that'd be a different story. I am unfortunately not aware of what functions the Ubuntu installer calls upon to probe for existing OSes.

Bottom of the line: It's the Ubuntu installer that does this, not the GRUB setup, whether invoked via the GUI or from a commandline.

---

### Post by balaknair on 2009-01-06
**@northern lights**

OK, thanks a lot.
That clears up a lot misconceptions I had.

> If you were to figure which tool does this and how to run it correctly outside the installer, that'd be a different story. I am unfortunately not aware of what functions the Ubuntu installer calls upon to probe for existing OSes.

That tool would be os-prober, a spin-off from the Debian-installer. 


[https://help.ubuntu.com/7.04/installation-guide/i386/modules-list.html](https://help.ubuntu.com/7.04/installation-guide/i386/modules-list.html)
>  os-prober

    Detects currently installed operating systems on the computer and passes this information to the bootloader-installer, which may offer you an ability to add discovered operating systems to the bootloader's start menu. This way the user could easily choose at the boot time which operating system to start.




[http://kitenet.net/~joey/code/os-prober/](http://kitenet.net/~joey/code/os-prober/)

> Some possible other uses include:

    * Use by other installers than d-i.
          o I've been told that Frugalware 0.5 will use it.
    [B]* Using os-prober to eg, generate a grub menu.lst file for a running system.
    * Use on a live CD or rescue disk to enumerate OSes[/B]


This page however has not been updated for some time now, and I was unable to find anything more relating to any progress on these 'possible other uses'.

Thanks for your input though. :D

---

### Post by northern lights on 2009-01-06
I had read your posts on the subject before also. I just didn't figure *os-prober* would be a separately installable package and runnable application.

It is though.

It does, when invoked, not write a new menu.lst on it's own.
I'm working on figuring out how to do this.

[EDIT]
The ubuntu-branch of development is hosted on Launchpad. [Here]("https://launchpad.net/ubuntu/jaunty/+source/os-prober/1.28ubuntu2")'s the jaunty os-prober source ( 1.2.8 ). The tarball contains a very useful readme. Anyhow, while os-prober can find other Linux installations, as well as other operating systems, it does not try to work out all the information needed to boot Linux (initrd, kernel params, etc). That task is left to *linux-boot-prober*.
Now going to check whether both tools can be incorporated in a script to rewrite a menu.lst
[/EDIT]

---

### Post by msfisher on 2009-01-06
First of all, you both have touched on something that I finally realized -- what I was looking for was not "rebuilding Grub" but "repopulating menu.lst". Great detective work Northern, and thanks to balak for first noticing os-prober.  

As I'm sure you've both found out, os-prober is not just in jaunty, but earlier versions as well, see [http://packages.ubuntu.com/feisty/os-prober]("http://packages.ubuntu.com/feisty/os-prober")
which includes links to other versions.

Both probers are listed by the install system team as of Feb 2008 ([http://people.ubuntu.com/~liw/lintian/hardy-i386-main/reports/maintainer/debian-boot@lists.debian.org.html]("http://people.ubuntu.com/~liw/lintian/hardy-i386-main/reports/maintainer/debian-boot@lists.debian.org.html")) about halfway down the page.

It seems like this whole thing has come up before in Debian: [http://www.mail-archive.com/debian-boot@lists.debian.org/msg82502.html]("http://www.mail-archive.com/debian-boot@lists.debian.org/msg82502.html") and subsequent thread entries.  This thread generated a bug report and patches.

I know a menu.lst builder is possible.  At work I've had to install Fedora 9.  Subsequent updates have caused two new kernels to be listed in the Grub menu along with the earlier ones.  I've noticed the same thing with Ubuntu.  I'm not a programmer by any stretch of the imagination, but it sounds like a combination of os-prober, linux-boot-prober and whatever tool rewrites menu.lst would do the job.  

Overall, it sounds like a good project for you guys!  Honestly, I look forward to trying out a utility which does what you/we have been discussing.

Thanks again for the responses and interesting discussion!

---

### Post by northern lights on 2009-01-06
Two news:

Ubuntu includes a binary package that does rewrite a menu.lst - *update-grub*
I remember running this in Feisty also. It is installed by default. It however does not depend on *os-prober* (which is not installed by default) and cannot possibly call upon either *os-prober* or *linux-boot-prober* because it finishes faster than a manually invoked *os-prober*. However, *update-grub* appears to only to search the *nix OS it is run from for installed kernels. I'm already on campus and only have my laptop with me (single OS), so I can't confirm with certainty.

Secondly, there is an sh script with ported code from *grub-installer* and *update-grub* designed for the Italian distro MediaNix (obviously also Debian based) called [gengrubmenu2]("http://trac.medianix.org/browser/morphix/trunk/gengrubmenu2/gengrubmenu2?format=raw").

I've got to head to class, I'll check further tonight. This is fun.

---

### Post by balaknair on 2009-01-09
@northern lights
You might have just about got it.

> **northern lights said:**
> Two news:

Ubuntu includes a binary package that does rewrite a menu.lst - *update-grub*
I remember running this in Feisty also. It is installed by default. It however does not depend on *os-prober* (which is not installed by default) and cannot possibly call upon either *os-prober* or *linux-boot-prober* because it finishes faster than a manually invoked *os-prober*. However, *update-grub* appears to only to search the *nix OS it is run from for installed kernels. I'm already on campus and only have my laptop with me (single OS), so I can't confirm with certainty.

Secondly, there is an sh script with ported code from *grub-installer* and *update-grub* designed for the Italian distro MediaNix (obviously also Debian based) called [gengrubmenu2]("http://trac.medianix.org/browser/morphix/trunk/gengrubmenu2/gengrubmenu2?format=raw").

I've got to head to class, I'll check further tonight. This is fun.


I know about update-grub. It works by looking in */boot* for all files starting with "vmlinuz-", and I think is how the GRUB menu.lst is modified after a kernel upgrade(adding the new kernel to boot options). But since it looks only in /boot for vmlinuz files, it would as you say detect only the OS it is run from(unless you have a separate /boot partition for multiple *NIX OSes).
> I know a menu.lst builder is possible. At work I've had to install Fedora 9. Subsequent updates have caused two new kernels to be listed in the Grub menu along with the earlier ones. I've noticed the same thing with Ubuntu. I'm not a programmer by any stretch of the imagination, but it sounds like a combination of os-prober, linux-boot-prober and whatever tool rewrites menu.lst would do the job.

That's(update-grub) what happens in Ubuntu during kernel updates.


But I doubt if that's the answer we're looking for, since it would not detect *other OSes* on a multiboot system. Maybe a script which invokes os-prober to scan the drives and then uses the output to generate a new menu.lst would fit the bill. 

From what I could understand, gengrub2 seems to do just this.

```
#Maybe there should be check if menu.lst already exist ?
echo $BC_GRUBTEMPLATE1 > $TARGET/menu.lst

**os-prober** > /tmp/os-probed || true

# Generation menu.lst addition for other OSes.
tmpfile=/tmp/menu.lst.extras
OLDIFS="$IFS"
IFS="$newline"
for os in $(cat /tmp/os-probed); do
	IFS="$OLDIFS"
	title=$(echo "$os" | cut -d: -f2)
	type=$(echo "$os" | cut -d: -f4)
	case "$type" in
		chain)
			partition=$(echo "$os" | cut -d: -f1)
			grubdrive=$(convert "$partition") || true
			if [ -n "$grubdrive" ]; then
				cat >> $tmpfile <<EOF

# This entry automatically added by the Debian installer for a non-linux OS
# on $partition
title		$title
root		$grubdrive
savedefault
EOF
				# Only set makeactive if grub is installed
				# in the mbr.
				if [ "$bootdev" = "(hd0)" ]; then
					cat >> $tmpfile <<EOF
makeactive
EOF
				fi
				cat >> $tmpfile <<EOF
chainloader	+1

EOF
			fi
		;;
		linux)
			partition=$(echo "$os" | cut -d: -f1)
			mappedpartition=$partition
			IFS="$newline"
			for entry in $(linux-boot-prober "$partition"); do
				IFS="$OLDIFS"
				bootpart=$(echo "$entry" | cut -d: -f2)
				mappedbootpart=$bootpart || true
				if [ -z "$mappedbootpart" ]; then
					mappedbootpart="$bootpart"
				fi
				label=$(echo "$entry" | cut -d : -f3)
				if [ -z "$label" ]; then
					label="$title"
				fi
				kernel=$(echo "$entry" | cut -d : -f4)
				initrd=$(echo "$entry" | cut -d : -f5)
				if echo "$kernel" | grep -q '^/boot/' && \
				   [ "$mappedbootpart" != "$mappedpartition" ]; then
				   	# separate /boot partition
					kernel=$(echo "$kernel" | sed 's!^/boot!!')
					initrd=$(echo "$initrd" | sed 's!^/boot!!')
					grubdrive=$(convert "$mappedbootpart") || true
				else
					grubdrive=$(convert "$mappedpartition") || true
				fi
				params="$(echo "$entry" | cut -d : -f6-) $serial"
				cat >> $tmpfile <<EOF


```

So the script uses os-prober to scan the drives and generates a new menu.lst? 
From what I could make out from
```
# this is code initally ported by Mantas Kriauciunas <mantas@akl.lt>
# for the Morphix project. The code came for a large part from the 
# grub-installer (taken from debian-installer) postinst script and
# update-grub script from the grub debian package.
# os-prober tool from debian-installer project is needed for finding
# other operating systems.

```

Now if only someone could modify gengrub2 for Ubuntu(it seems a bit Medianix specific, will it work 'as is' in Ubuntu?) and add a GUI for us point and click types... :D

---

