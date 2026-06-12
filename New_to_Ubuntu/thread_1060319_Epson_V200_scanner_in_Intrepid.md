---
title: "Epson V200 scanner in Intrepid?"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by 2CV67 on 2009-02-04
**Edit: Skip to post #23 to find what worked for me** :)

There is already a thread on Epson V200: [http://ubuntuforums.org/showthread.php?t=892351](http://ubuntuforums.org/showthread.php?t=892351) but since it is now called > [SOLVED] Epson V200 scanner &amp; Hardy I think a new start is justified!

There is a lot of good information in the old thread, particularly from Tanker Bob & including a link to his guide [here]("http://reformedmusings.wordpress.com/2008/12/13/fixing-epson-scanners-in-ubuntu-810-intrepid-linux/").

I think several of us are still stuck with about the same symptoms though.

My own case is as follows (copied from old thread - excuse cross-posting)

> I started this thread for my V200 in Hardy & have just upgraded to Intrepid & lost my scanner.

I followed the very clear track from Tanker Bob here - thanks!

I have user priviledges for the scanner OK.

lsusb finds it OK.

Synapt shows everything there except libsane-extras
Trying to install that leads to Error messages (attached) & so **no installation of libsane-extras**.

Didn't do any special installs or restarts.

sane-find-scanner finds it OK.

scanimage -L does not find it.

sudo scanimage -L does find it...

/usr/bin/iscan leads to an error.
sudo /usr/bin/iscan works just fine.

It sounds like a simple permissions problem.
I rechecked that in Users & Groups I DO have scanner permission.
I have not started inventing files or anything fancy, since the thing works for sudo...


Thanks for any advice!

---

### Post by 2CV67 on 2009-02-05
In a parallel Ubuntuniverse -  [http://ubuntuforums.org/showthread.php?t=892351](http://ubuntuforums.org/showthread.php?t=892351)  -  Tanker Bob kindly suggested > It still sounds like a permission issue. Try giving yourself permission to everything to do with USB devices, logout/in, and see what happens. If that doesn't work, try giving yourself permission for everything, logout/in, and see. I think that there has to be some errant permission laying around ambushing you.

I tried that.
In System > Admin > Users & Groups > me > Properties > User Priviledges - I already had "Use scanners" enabled (carried over for years) as well as everything except faxes & tapes (& wireless - that's odd...).
But I unticked scanners & rebooted, then reticked scanners & rebooted - no change.
Then I ticked everything & rebooted - still no change.

So now I know I failed to install libsane-extras, which supposedly contains stuff needed to run Epson scanners, but I see behaviour which suggests a permissions problem.

Is there any way I can pin this down better, or any way I can get libsane-extras to install? (see error messages in initial post).

Thanks for any suggestions.

---

### Post by 2CV67 on 2009-02-05
I still have Hardy LTS on another partition on the same PC & the scanner still works OK in Hardy...

I tried comparing all kinds of stuff between Intrepid & Hardy, particularly the items in posts #11 & #23 in this thread on iscan:
[http://ubuntuforums.org/showthread.php?t=20992](http://ubuntuforums.org/showthread.php?t=20992)

Basically, everything I checked so far looks the same.
Same permissions.
Same absence of libsane-extras
Same versions of iscan 2.8.0-2 & iscan-plugin-gt-f670 2.0.0-2
Same presence of epkowa in /etc/sane.d/dll.conf
Same presence of /etc/sane.d/epkowa.conf
Same settings in /etc/hotplug/usb/iscan-device
- DEFAULT OWNER=root
- DEFAULT GROUP=root
- DEFAULT PERMS=0666

I did see a slight difference in /etc/sane.d/dll.conf
- Hardy has:
- - epkowa
- - epson
- - #epson2
- Intrepid has:
- - epkowa
- - epson
- - epson2

I tried commenting out #epson2 - no change
I tried commenting out #epson as well - no change
I tried changing /etc/hotplug/usb/iscan-device to:
- DEFAULT OWNER=user - no change

I have left those changes installed for now.

I have run out of ideas again!

---

### Post by Tanker Bob on 2009-02-05
Under System -> Administration -> Users and Groups, I Unlocked the permissions, then clicked on Manage Groups. I found 2 scanner-related groups: scanner with Group ID 104 and saned with Group ID 123. I am members of both groups on these screens. You might check those. Other than that, I'm not sure what to suggest. I had to scan as root in Feisty, but not in Hardy or Intrepid.

---

### Post by 2CV67 on 2009-02-05
Thanks for your patience!

I am member of both groups; scanner - ID 105 & saned - ID 124.

Looking at something "simple" - I am trying to see how/why I can lauch iscan by clicking on /usr/bin/iscan in a root nautilus screen but not in my own nautilus.
I saw root had r/w permissions but root group & others ro.
There is a tick in "Allow executing file as program"
I tried r/w permissions for all - no change.

Hmmm...

---

### Post by Tanker Bob on 2009-02-05
Make sure that you log out and back in after making permission changes. In my experience, they don't "take" otherwise.

---

### Post by 2CV67 on 2009-02-05
Thanks for that good observation.

In fact, I have generally been doing cold reboots between investigations, partly for config files to 'take' & partly because it's the only way to turn the scanner off - just in case that might be part of the problem - although it does not seem to be a problem hot-rebooting between Hardy & XP.

I'll keep plugging away...

---

### Post by emperor on 2009-02-05
> **2CV67 said:**
> Thanks for your patience!

I am member of both groups; scanner - ID 105 & saned - ID 124.

Looking at something "simple" - I am trying to see how/why I can lauch iscan by clicking on /usr/bin/iscan in a root nautilus screen but not in my own nautilus.
I saw root had r/w permissions but root group & others ro.
There is a tick in "Allow executing file as program"
I tried r/w permissions for all - no change.

Hmmm...

Is the execute (x) permission set for non-root access? For example:

-rwxr-xr-x

You can set the permissions using "chmod". For example:

sudo chmod 755 /usr/bin/iscan

e.p.

---

### Post by 2CV67 on 2009-02-06
Thanks for that good question emperor.

Trying to do everything by GUI - I couldn't see anything about execute permissions.
See first attachment for apparent permissions.
I eventually found I needed to:
Applications > System Tools > Configuration Editor > Apps > Nautilus > Preferences > Show Advanced Preferences > Tick

Now I can see that everybody has rwx permissions...
See attachment 2.

:confused:

---

### Post by emperor on 2009-02-06
run iscan from a terminal session and see if any messages are printed that might give a clue to the problem.

you@host: $ iscan

---

### Post by 2CV67 on 2009-02-06
No messages in terminal.

It just throws up the usual little window with "Could not send command to scanner. Check the scanner's status" - see attached.
Just like when I run "/usr/bin/iscan".

The scanner is switched on, of course & responds OK to "sudo /usr/lib/iscan".
...and to simply "sudo iscan" I just found out!

---

### Post by emperor on 2009-02-06
Check the permission on "libsane-epkowa.so.x.x.x (your installed version)

First use locate to find out where it's installed and the library version that installed. You need to check the rights on the actual library file and NOT the symbolic link at "epkowa.so.1".

If locate fails to run you will need to build the database:  sudo updatedb

emperor@linXos:~$ locate epkowa
/etc/sane.d/epkowa.conf
/usr/lib/sane/libsane-epkowa.la
/usr/lib/sane/libsane-epkowa.so.1
/usr/lib/sane/libsane-epkowa.so.1.0.15
/usr/share/man/man5/sane-epkowa.5.gz

emperor@linXos:~$ ls -l /usr/lib/sane/libsane-epkowa.so.1.0.15
-rw-r--r-- 1 root root 191200 2008-12-07 19:16 /usr/lib/sane/libsane-epkowa.so.1.0.15

You only need read 'r' rights, you need the last field to contain a 'r'.

To fix the permissions: sudo chmod 644  /usr/lib/sane/libsane-epkowa.so.1.0.15

I know I had to fix something like this after I installed iscan on Ubuntu 8.10; just a little fuzzy right now!

---

### Post by 2CV67 on 2009-02-07
Emperor - I **_really_** appreciate your fully detailed help!

But we don't seem to be there yet...

I have libsane-epkowa.so.1.0.15 located in /usr/lib/sane

It looks like the permissions are already OK -rwxr-xr-x.
See attached.

.....?

---

### Post by emperor on 2009-02-07
See if you have this file: "/etc/udev/iscan.rules".

This is the rule file that sets the USB device entry to "scanner" group.

If the file is present check that there is a symbloic link to it in "/etc/udev/rules.d".

I have the following:

emperor@linXos:/etc/udev/rules.d$ ls -la *_iscan.rules
lrwxrwxrwx 1 root root 14 2008-12-27 18:40 z60_iscan.rules -> ../iscan.rules

The "*.rules? files are processed in lexical order, so the leading "z" will insure that the iscan rule file runs last. Not sure why this was done as "60" must have been the original (order) intent.

e.p.

---

### Post by emperor on 2009-02-07
One other thing you might do  is check all privileges in  user account "User Privileges" tab.

System - Administration - Users and Groups, then unlock your user account and select properties, then the User Privileges" tab.

Not all the groups are shown in the group editor list like "plugdev". Ubuntu is hiding some of the group names.

To see all the group names look at the contents of /etc/group (look but don't edit).

$ cat /etc/group

-e.p.

---

### Post by 2CV67 on 2009-02-08
You can't imagine how much I appreciate your continuing interest!

I don't have: "/etc/udev/iscan.rules"
See screenshot of contents of /etc/udev - not much.

I searched Nautilus File System for  "iscan.rules" & found nothing.

As a comment, my Hardy installation does not have "iscan.rules" anywhere either & I just rechecked I can launch iscan perfectly there, just by: Terminal > iscan.

As part of this thread, I gave myself all possible permissions - see screenshot.

I did not fully understand what you were getting at with looking at the extra groups not shown in Users & Groups window.

Here is the contents of /etc/group:```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:chris,yyyy
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:chris,yyyy
fax:x:21:yyyy,chris
voice:x:22:
cdrom:x:24:chris,yyyy
floppy:x:25:chris,yyyy
tape:x:26:yyyy,chris
sudo:x:27:
audio:x:29:pulse,chris,yyyy
dip:x:30:chris,yyyy
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:chris,yyyy
sasl:x:45:
plugdev:x:46:chris,yyyy
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
dhcp:x:102:
syslog:x:103:
klog:x:104:
scanner:x:105:hplip,root,yyyy,chris
nvram:x:106:
fuse:x:107:chris,yyyy
ssl-cert:x:108:
lpadmin:x:109:chris,yyyy
crontab:x:110:
mlocate:x:111:
ssh:x:112:
avahi-autoipd:x:113:
gdm:x:114:
admin:x:115:chris,yyyy
pulse:x:116:
pulse-access:x:117:
pulse-rt:x:118:
messagebus:x:119:
avahi:x:120:
netdev:x:121:chris
polkituser:x:122:
haldaemon:x:123:
chris:x:1000:
saned:x:124:chris,root
yyyy:x:1001:
guest:x:125:
```

I am way out of my depth here....

---

### Post by emperor on 2009-02-08
What version of iscan did you install? 

When I go to the AVASYS website, you get directed to an old iscan v 2.8 package  if you select the V200 scanner and newer packages if you select my printer the Perfection 2400 PHOTO. There is even pre-built Ubuntu 32/64 bit deb packages for the 2400.

[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

So, if you installed the older package, uninstall it and install the appropriate 2.15 version.

---

### Post by 2CV67 on 2009-02-08
Yes, I mentioned in post #3, I have iscan 2.8.0-2 & iscan-plugin-gt-f670 2.0.0-2

I had these running OK in Hardy (& Gutsy, I think with the same ones).

I checked the avasys site where they had nothing newer for the V200.

I guess I am hesitating about jumping through new hoops installing a package not even recommended for my scanner...
Is that a stab in the dark on your part, or is it justified by knowledge or experience? (excuse that question!)

Do other people have the V200 working with iscan 2.8.0 or with 2.15..?

Should I stick with the same plugin (presumably)?

On a completely different tack while waiting - is there any way of getting a trace or log report on the attempt to activate iscan either from the terminal or GUI?
Something like the "ping" thing for wireless?
So you could see where it is trying to go & what stops it?

I looked inside iscan (with "strings") hoping to find an address it was heading to, but could not recognise much!
The only thing that looked promising was ```
ppath
!before
*ppath <= before
invalid mutex handler registration
invalid search path insert position
dirnam[(((dirnam) && (dirnam)[0]) ? strlen (dirnam) : 0) -1] != '/'
before - *ppath <= strlen (*ppath)
/lib:/usr/lib:include:ld.so.conf.d/*.conf:/usr/X11R6/lib
.libs/
``` but that didn't help me much!

It really is frustrating that "iscan" & "scanimage -L" work for sudo but not without.
Other people in the previous thread got to that position too, but never said if/how they got any further!

---

### Post by emperor on 2009-02-08
iscan v2.08 was just the first version that had support for the V200. See attached NEWS file from source.

You should use the same plugin file.

Note: There is a chance that the plugin will not work with iscan 2.15 as I have no way to test it!

The advantage to using the offical deb on the download site is that any scripts that are part of the install are preserved. When the RPM is converted to a DEB using alien, the scripts are not converted by default. Alien can convert the scripts if the "-c" parameter is specified. The scripts are not automaticly converted due to that fact that some need to be re-written for the new target distribution.

Also, "iscan.rules" is in v2.15.

run:
ltrace iscan - for a library trace
strace iscan - for a stack trace

You may need to install ltrace and strace using apt or synaptic

e.p.

---

### Post by emperor on 2009-02-08
You could try this instead of installing the newer 2.15 deb file.

Manual add the iscan.rules to /dev/udev

sudo cp iscan.rules /etc/udev

(owner:group should be root:root)

sudo chown root:root iscan.rules

Then make the symbolic link in the rules.d directory:

sudo ln -s /etc/udev/iscan.rules /etc/udev/rules.d/z60_iscan.rules

To make sure the rules are picked up immediately:

 sudo udevadm control --reload_rules

I have attached the iscan.rules file.

---

### Post by emperor on 2009-02-08
After looking at the contents of both the v2.8 rpm and the v2.15 deb package, I recommend that you install v2.15. The newer package is setup to install and work properly in the Linux kernel used in Ubuntu 8.10.

---

### Post by herdivet on 2009-02-09
I fixed this problem by editing the line in /etc/udev/rules.d/45-libsane.rules  where I put in the information for the scanner.  The original instructions say you should have an entry with SYSFS{idVendor}==... , MODE="664", GROUP...  I changed the 664 to 666 and was able to run the scanner without using sudo.

I don't know if this will help you, but it did solve this problem for me.  It may not be the best solution, but it's the only one I've found that worked.  Of course, I also stopped looking once this worked :>

---

### Post by 2CV67 on 2009-02-09
Firstly I must apologize profusely to emperor for maybe doubting his authority!  :oops:  :oops:

I now feel I understand things better.

I will probably update to 2.15 soon.

In the meantime, I noted herdivet's comment & decided to try that first, as it looked simple & reversible.

I backtracked through his & boddhisatva's posts in the earlier thread [here]("http://ubuntuforums.org/showthread.php?t=892351").

I created a file /etc/udev/rules.d/45-libsane.rules

I copied in:```
 # Epson Corp.|Perfection V200 Photo
 SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="012e", MODE="664", GROUP="scanner"

``` from [here]("http://ubuntuguide.org/wiki/Dapper#Setting_up_USB") as it matched the output of lsusb.

Rebooted & VOILA!!!

I now have iscan & Xsane working just like they always should have...

Conclusions: 
Ubuntu & Epson still have a very long way to go towards plug-&-play.
The quality & reactivity of Forum Members here is amazing!

Many, many thanks to Tanker Bob, Boddhisatva, Emperor & Herdivet!

---

### Post by 2CV67 on 2009-02-09
> **emperor said:**
> iscan v2.08 was just the first version that had support for the V200. See attached NEWS file from source.

You should use the same plugin file.

Note: There is a chance that the plugin will not work with iscan 2.15 as I have no way to test it!

That was a neat NEWS file - I have not managed to find it myself...

It does suggest in there that the V200 plugin might not work with the latest version of iscan.

I dug about a bit on the Avasys site & they are quite definite about that.
[http://avasys.jp/hp/page000001200/hpg000001112.htm](http://avasys.jp/hp/page000001200/hpg000001112.htm)
> Plugin package incompatibility with Image Scan! for Linux (version 2.11.0)
QA

As of iscan-2.11.0, only plugins with a version of 2.1.0 or higher can be used.

This means that the following plugins can no longer be used:
   iscan-plugin-cx4400-2.0.0-0
   iscan-plugin-gt-7200-1.0.0-1
   iscan-plugin-gt-7300-1.0.0-1
   iscan-plugin-gt-9400-1.0.0-1
   iscan-plugin-gt-f500-1.0.0-1
   iscan-plugin-gt-f520-1.0.0-1
   iscan-plugin-gt-f600-1.0.0-1
  **_ iscan-plugin-gt-f670-2.0.0-1_**
   iscan-plugin-gt-f700-2.0.0-0
   iscan-plugin-gt-s600-2.0.0-1
   iscan-plugin-gt-x750-1.0.0-1

If you need any of the above plugins, please use iscan-2.10.0 or the version available from the download page for your model(s). 

So they say V200 should only be used with iscan up to 2.10.0
According to your NEWS file, the only differences between my 2.8.0  &  the latest useable version are support for other models.
So I guess I will stay where I am now that everything is working! :D

I would certainly mark this thread [Solved] now if I could...

Thanks for pointing out the strace & ltrace utilities which I had never heard of, inspite of much Googling!
They sound very useful, but having tried them I have to say the results are not obviously useful to dummies!
I will play a bit more...

---

### Post by herdivet on 2009-02-09
I'm glad you [finally] got it working.  I don't think any OS is actually plug and play, I've had similar problems with others as well.  The big advantage Ubuntu has is the forums, it's like someone on call 24x7 with answers and suggestions, but with no 800 number and hours on the phone having someone tell you to unplug the computer and plug it back in...

---

### Post by emperor on 2009-02-09
Glad you found the info concerning the plugin compatibility.

The iscan.rules file includes the string you put in the 45-libsane.rules file you created as well as entries for the other epson scanners. For a universal solution for those scanners that require a plugin, renaming the file to say "45-iscan.rules" and putting it in the /etc/udev/rules.d directory would work.

It may also be that iscan version 2.10 supports udev and will install the iscan.rules file automaticly. I have not been able to find v2.10. If anyone does, open the rpm with file-roller and see if it supports udev; has a ".rules" file inside.

Note: The NEWS file came from the source tarball.

---

### Post by 2CV67 on 2009-02-09
> **herdivet said:**
> ...I don't think any OS is actually plug and play, I've had similar problems with others as well.  The big advantage Ubuntu has is the forums, it's like someone on call 24x7 with answers and suggestions, but with no 800 number and hours on the phone having someone tell you to unplug the computer and plug it back in...

What you say is true, especially about the forums, but...

I am a very strong supporter of Ubuntu, both philosophically (because it's free & it isn't monopolistic Microsoft) and practically (because so much of it works so well, because it's adaptable, because I enjoy the challenge & because of the strong friendly community).

But it still can't compete with Microsoft in terms of easy, no-brain, plug-&-play functionality & (in my experience) bullet-proof reliability.
I know it is not fashionable to say that sort of thing here, but if the community is in denial of that fact, then ultimate success with the general public is still a long way off.
The only problem you can't solve is the one you refuse to see.

I have been using W95 then XP since 1995 and every modem, printer, scanner, wireless-dongle, pci-card, EHD, flash-drive & camera I have thrown at it has just plugged in & worked.
Of course I know that is because they have to develop them to do just that.
I have been learning Ubuntu for 2 years & in that time wireless, printing & scanning have been a continuing horrendous battle.
A battle that starts again every 6 months with the latest & greatest new Ubuntu version.
Which has quite often left me with a totally-unusable Linux relying on XP to get onto the internet a find solutions.
At first, I accepted that the Inventel USB dongle, the HP Scanjet 4470c scanner and the Canon BJC 6000 printer, inherited from XP, were just unlucky choices, so I gradually replaced them by supposedly-work-straight-out-of-the-box items – Edimax 7128g PCI card, Epson V200 scanner & Canon iP4300 printer.
If you have a lot of time to spare, you can browse the 378 posts in 84 threads I have needed to contribute to, to get & keep them working, not counting the ten times as many threads I read without joining & the thousands of Google searches.
This is OK for me, as I enjoy it like I enjoy doing puzzles, but there is no way I could recommend Linux to any non-geeks (like my 4 daughters) who just need a PC that works.
Not yet.
I hope we get there soon!

All this said with no bitterness, but with a strong desire to improve things!

Thanks again & again to everybody on this forum!

---

### Post by emperor on 2009-02-10
[quote=2CV67;6705906
This is OK for me, as I enjoy it like I enjoy doing puzzles, but there is no way I could recommend Linux to any non-geeks (like my 4 daughters) who just need a PC that works.
Not yet.
I hope we get there soon!
[/quote]

It does takes a resident geek to keep the computers running and updated with Linux; in my home it is me. Both my wife and daughter use Linux about 95% of the the time. My wife runs XP in a virtual machine when she needs Office for her MBA cources and my daughter dual boots with XP when she needs to use PhotoShop for some of her art work or school projects; both are using Ubuntu 8.04 LTS. The LTS version is a better solution for those who just want a computer to work and don't enjoy working disruptions every 6 months.

Linux is getting better and easier to use all the time but I do not expect the masses to use it regularly any time soon; especially if Windows 7 turns out to be a real improvement over Vista. I usually recommend OSX to people who just want a computer to work and are not ready for the Linux Experience!

e.p.

---

### Post by viajador on 2009-02-15
THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU!!!!
:popcorn:

You have no idea how frustrated I was getting! I hate when I have everything pinned down (with text files logging how everything was acomplished) and then, just by upgrading to a newer version of Ubuntu, stuff stops working!

I had this weekend setted aside for scanning some photo work, I had everything installed as I usually do, and then... it only works with sudo! I was getting so angry... and then I found your own struggle and how you got people guiding you to the right solution!

Once again: thank you!

:)

---

### Post by 2CV67 on 2009-02-15
Sounds like another satisfied customer for the forum!! :D

I am sure all contributors here feel nice & warm inside now...
Thank YOU!

As a reaction to your comment on newer versions screwing things up to a greater or lesser extent - my own new-found solution is to keep both my latest-update version & an LTS version working in parallel.
Then I can always fall back on the LTS version until the latest version is up & running correctly.
And I even have a live DVD of LTS with all my bells & whistles in case of BIG problems.
Certainly overkill - but very useful & who is short of Hard Drive space these days?.

[See this thread.]("http://ubuntuforums.org/showthread.php?t=1038213")
Skip to post #12 if you don't want to read the book.

Thanks for your feedback.

---

### Post by boddhisatva on 2009-02-23
I didn't know how to subscribe to this thread without posting, so I'm posting this. My v200 is working fine in Intrepid after using community help and a bit of my brain on the thread for Hardy, which 2CV67 has reasonably transferred to this thread for Intrepid. I want to stay updated on the discussion and perhaps contribute, if my very basic linux skills allow. And anyway, you never know how long the scanner is going to work seamlessly, with all the updates and 9.04 in sight...
So it's better to stay informed :)
By the way, I strongly agree with 2CV67 that you can't solve a problem if you refuse to see it. Ubuntu (and Linux in general) is a brilliant system, but I've had my share of trepidation and frustration over different issues. Not everybody is as enthusiastic and patient, and "monopoly-aware" as we are, so we can't expect people to change a system, even if we see its superiority, if it doesn't meet some basic criteria of reliability and ease of use. Not everybody has to be a geek, obviously. Not many people are idealistic enough to cause themselves trouble with the remote loftly aim of oposing a monopolistic giant... And few people are even remotely aware of the limitations to their freedom that M$ monopoly entails, as they haven't tasted anything else. It reminds me of communist times in Poland, where everybody lived in the same kind of flat and drove the same car. People didn't feel all that deprived, because that was what everybody did, they weren't aware of other possibilities. Unless someone travelled abroad..
Sorry for the digression, I just couln't resist... :)

---

### Post by eeried on 2009-04-27
Many thanks to all on this thread, as I hope to make V200 work with Jaunty too.

I don't agree with what some of you say here about M$ being easier than GNU/Linux. M$ might be easier only when hardware manufacturors do their job of providing drivers. The Gnu/Linux community with the help of some manufacturors provide an awful lot of drivers. 

I installed Hardy for someone who has 2 all-in-one HP, one old, one new and an epson scanner. He was impressed as all the hardware was installed at once. Xsane had the 3 scanners ready for use. I haven't used M$ for nearly 5 years but if CD-rom are still needed for printers and scanners, I don't see why such an OS is called plug and play.

> **emperor said:**
> It does takes a resident geek to keep the computers running and updated with Linux… my daughter dual boots with XP when she needs to use PhotoShop for some of her art work or school projects; both are using Ubuntu 8.04 LTS. The LTS version is a better solution for those who just want a computer to work and don't enjoy working disruptions every 6 months.

I'm no geek at all and I maintain nearly a dozen computers in our tiny LUG, and I find a lot of help on the web anyway. M$ would be hell to maintain, what with spyware and viruses. In fact our newbie members update the (X)Ubuntu computers themselves, and I maintain the 3 computers running Slitaz or Puppy.

It is a pity young people don't use GIMP which does the job.

I agree though that the LST is a good solution. The October releases hardly seem stable (edgy and Intrepid weren't satisfactory.

Many thanks anyway for all the help on this thread and the previous one. I'll report as soon as I can get my hands on the V200 scanner.

---

### Post by boddhisatva on 2009-05-16
Has anyone managed to get the scanner working in Jaunty? I've tried the steps for Intrepid, and they don't seem to work...

---

### Post by boddhisatva on 2009-05-16
It seems I have the same problem 2CV67 used to have in Intrepid: iscan only works in sudo mode. I tried to trace 2CV67's steps, but it seems eventually creating 45-libsane.rules did the trick, or am I wrong? Now creating 45-libsane.rules doesn't seem to help - I can still only run iscan as sudo. It seems like this scanner business will be the main "attraction" of each system upgrade :)

---

### Post by 2CV67 on 2009-05-16
Just to confirm what worked for me in Intrepid:> I created a file /etc/udev/rules.d/45-libsane.rules

I copied in:
Code:

 # Epson Corp.|Perfection V200 Photo
 SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="012e", MODE="664", GROUP="scanner"

from here as it matched the output of lsusb.

Rebooted & VOILA!!!

I now have iscan & Xsane working just like they always should have...

Sorry I can't help with Jaunty as I am a deliberate "late adopter" of upgrades due to this kind of problem.

But I shall be watching this thread with bated breath, hoping to see a solution before I need it!

---

### Post by boddhisatva on 2009-05-17
That worked on Intrepid, now it doesn't. I can run iscan as sudo, but then it seems to scan much more slowly. And it only has the option to save as pnm or jpg, png and tiff are disabled.

---

### Post by boddhisatva on 2009-05-18
I've converted the **iscan-2.8.0-1.c2.i386.rpm** package (for gcc 3.4 or later) with **alien** with the --scripts option. When I ran the .deb, it created a 60-iscan.rules file, which lists all the possible products - I don't think it was there when I ran **alien** without the --scripts option. 

> # This file is part of the "Image Scan! for Linux" binary package (or
# generated automatically as part of its installation).  Any changes
# will be overwritten with each upgrade of the package.

ACTION!="add", GOTO="iscan_rules_end"
SUBSYSTEM!="usb_device", GOTO="iscan_rules_end"

SYSFS{idVendor}="04b8" SYSFS{idProduct}="0101" MODE="0666"
...
[COLOR="Blue"][all the product ids listed here][/COLOR]
...

LABEL="iscan_rules_end"


My scanner is SYSFS{idVendor}="04b8" SYSFS{idProduct}="012e" MODE="0666".
**Still, it isn't working. It works with sudo, but slowly and with pauses.** 
Any idea out there in the Universe? ;)

---

### Post by boddhisatva on 2009-05-23
They've posted new drivers for the scanner at avasys.jp. There's even a ready-made .deb package. There's a problem with dependencies: libltdl3 is not present in 9.04 repository (or in 8.10 for that matter), but you can download it here: [http://packages.ubuntu.com/hardy/i386/libltdl3/download]("http://packages.ubuntu.com/hardy/i386/libltdl3/download")
The driver is still not working without sudo, but at least it's now working A LOT faster (it worked REALLY slowly in 9.04 on the old driver) - it's even faster than the old driver on 8.10. So there's hope and (this is to 2CV67 and others) there's a reason for switching to 9.04 - once you find out how to get round the sudo problem of course :)
Typing sudo before starting GIMP (from which I've always scanned anyway) is not such a big problem for me, but of course it would be nice to have it running without additional hassle (such as having the scanned images saved with 'root privileges', which I then have to change). 

I've started a new thread for Jaunty, so perhaps the ongoing discussion about this wonderful scanner (and it's less-than-wonderful driver support) could move there:
[URL="http://ubuntuforums.org/showthread.php?t=1161947"]epson perfection v200 on Jaunty
[/URL]

---

### Post by boddhisatva on 2009-05-23
I've tried using xsane and unlike previously, when it said only 'cannot connect to scanner", now there's a message 
> open of device epkowa:interpreter:001:003 failed: Access to resource has been denied

And, unlike previously in Intrepid, scanimage -L seems to recognize scanner (without sudo):
> device `epkowa:interpreter:001:003' is a Epson (unknown model) flatbed scanner

" Access to resource has been denied" would suggest privileges, but I've tried all the suggestions for groups and privileges in the threads and it doesn't seem to help.

---

### Post by ^_Pepe_^ on 2009-11-04
Hi!

Just to avoid this threat to sink...

I've upgraded to 9.10 from 9.04, (and before 8.04 to 8.10, 8.10 to 9.04) in same installation, and yesterday I've discovered that my Epson V200...fails again.

Anyway sudo iscan make me the work. 

I was too busy to recover this old post (now, at work I finally found it).

I'll come back tonight with fresh news if tweak of 2CV67 (pretty car...btw) works or not.

[INDENT][I]Quote:
I created a file /etc/udev/rules.d/45-libsane.rules

I copied in:
Code:

# Epson Corp.|Perfection V200 Photo
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="012e", MODE="664", GROUP="scanner"

from here as it matched the output of lsusb.

Rebooted & VOILA!!!

I now have iscan & Xsane working just like they always should have... [/I][/INDENT]

Absolutely, this Epson is everything but plug&play... ;)


Regards,
^_Pepe_^

---

### Post by ^_Pepe_^ on 2009-11-04
OMG!

9.10 is horrible up to now! I can count more than 5 bugs affecting directly to me! :-(

Well...one more! V200 doesn't work without sudo command in 9.10.

Any idea/suggestion?

There's no scanner group in my users panel

Regards
Pepe

---

### Post by ^_Pepe_^ on 2009-11-04
Hi again!

For some reason, libsane & libsane-extras, were not installed through synaptic, so that was the problem

So these are the steps:

1. Check your user has permission to use scanners. 
2. Download iscan and plugin from here [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do). Now, we have .deb
3. Ensure that sane, sane-utils, libsane, and libsane-extras are ALL installed, as told here ([http://reformedmusings.wordpress.com/2008/12/13/fixing-epson-scanners-in-ubuntu-810-intrepid-linux/](http://reformedmusings.wordpress.com/2008/12/13/fixing-epson-scanners-in-ubuntu-810-intrepid-linux/))
4. Add the line "epkowa" to /etc/sane.d/dll.conf
5. Open this file /etc/udev/rules.d/45-libsane.rules and code:

[INDENT][INDENT]```
# Epson Corp.|Perfection V200 Photo
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="012e", MODE="664", GROUP="scanner"
```[/INDENT][/INDENT]

6. Reboot.

That should work. All credits to all users who worked here. I just summarize and fighted against 9.10 :-(. Now I'm going to investigate why I don't have starting sounds, but sound in videos...

Regards
^_Pepe_^

---

### Post by herdivet on 2009-11-16
I followed the instructions in this thead:

[http://ubuntuforums.org/sho](http://ubuntuforums.org/sho)
wthread.php?t=1200623

with great success.  I did have to reboot before it worked without sudo, but it worked without having to edit the epkowa line in libsane.d.

The BEST part is, it worked in Ubuntu 9.10 64 bit!!

---

### Post by boddhisatva on 2011-05-02
I downloaded the latest packages for Natty, but they didn't work. So I installed the previous packages (which worked on Maverick) and they do work!

The packages are called:
iscan_2.24.0-4.ltdl7_amd64.deb
iscan-plugin-gt-f670_2.1.0-3_amd64.deb

---

### Post by ^_Pepe_^ on 2011-05-04
> **boddhisatva said:**
> I downloaded the latest packages for Natty, but they didn't work. So I installed the previous packages (which worked on Maverick) and they do work!

The packages are called:
iscan_2.24.0-4.ltdl7_amd64.deb
iscan-plugin-gt-f670_2.1.0-3_amd64.deb

Hi!

I could only find 1.8.1-1 in [http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do). Where did you find 2.24 version?

Just for curiosity, because I get my server in 10.04...+

Thanks
^_Pepe_^

---

### Post by boddhisatva on 2011-05-04
The packages are no longer on avasys page. Luckily I backed up the previous deb packages that I had downloaded for 10.10. The current version of the core packages is 2.8, while 1.8 is the version of the DATA packages.
If anyone needs those previous (working) packages I can put them up for downloading.
Unfortunately, only for 64 bits.

---

