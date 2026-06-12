---
title: "Personal Setting Start Up Issue"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by kaspar_silas on 2010-03-17
Hi guys,

I have a weird problem that hopefully someone can solve or point me in the right direction anyway. 

So, I installed the ubuntu 9.10 netbook remix on an Asus 900. Then I removed the clutterish laucher and switched to a more standard desktop. 

Finally I moved home to an SDHC drive (always inserted) and altered fstab to automount this drive. This seemed to work okay at first however for no obvious reason I now get three lines like this at boot:

[  8.064417] sd 2:0:0:0: [sdc] Assuming drive cache: write through

sdc is of course the SDHC drive. 

Then after log in when the X server loads I also now appear in the default desktop (shown below) rather than my own one. Admittedly this is just a change of background and panel icons but it's annoying all the same. I can reload my personal settings if I log back in after restarting X using the command:

sudo /etc/init.d/gdm restart  

However clearly double logging in is not the elegant solution. So does anyone know what is? Cheers for any help

---

### Post by kaspar_silas on 2010-03-18
O and one more bit of information. Compiz also doesn't start in case that gives anyone any ideas.

---

### Post by kaspar_silas on 2010-03-22
Okay I worked out the problem, well I think so, feel free to correct my explanation. It's just given in the unlikely case it's helpful to anyone else.

I had this line to mount my flash drive in /etc/fstab

% /dev/sdc1 /media/FLASKHOME ext2 errors=remount-ro 0 2

Well originally I had the UUID version of the above but that hardly matters. I also had a symbolic link from /media/FLASHHOME to /home/[MYNAME]. Both of these fudges were solely to allow me to use a detachable home.

However the fstab mount failed during boot. Hence the system loaded up using / as home. At some stage I must have made some folders in / to allow booting up (thou I don't remember this). Hence I loaded into the standard home screen.

Now, on log in I check for drives in fstab not mounted and, well, mount them. Hence, logging in was fixing the mounting issue and making me blissfully unaware of it. Restarting X or logging out and in again moved the directory used as home to the correct one.

The simple solution that avoided the crappy double log in was to change the fstab line to:
% /dev/sdc1 /media/FLASKHOME ext2 errors=remount-ro 0 0

I understand that Setting the last 2 to 0 stops the fsck check. Hence I am guessed the fsck encountered errors and stopped the boot time mounting. This seems a pretty bad thing to solve a check reporting an error by turning off checking but then again it works. So unless anyone has any brighter ideas I'll live with it.

---

