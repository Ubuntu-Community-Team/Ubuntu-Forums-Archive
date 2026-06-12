---
title: "MSHOME / Windows Network unavailable after installation 8.04 LTS"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by TRBD16Z6 on 2008-06-22
I'm having some difficulty understanding why my Laptop will have perfect network access running the live cd but when I install to HDD it just dissapears. Running live I can have complete access to all shares and printers, but when its installed to the HDD, all I get is the Windows Network Icon under network places and it doesn't get and further than that. No MSHOME available. I've gone even so far as to try the new openSUSE 11.0 and is does the exact same thing. Below are a few other things I've tried.

- I can mount the shared folders if I type in smb://hostip/sharefold
- smbtree in terminal displays nothing after install but show everything on live cd.
- Internet works perfectly fine on both instances.

This is the system setup.

Acer Aspire 5600
 -Intel 1.66 core duo
 -1GB Mem
 -120GB HDD
 -Intel ipw3945 Wireless

Dual boot
 - Windows XP
 - Ubuntu 8.04 LTS i386

If some one could give me some help that'd be great. I've tried endless searching and fiddling with crap, editing smb.conf and other files. And reinstalling numerous times, along with try different Distro's.

Thanks in advance.

---

### Post by TRBD16Z6 on 2008-06-23
Do I need to list anything else.

The only other thing I can think of is that MSHOME is available if I connect a lan cable vs. the going wireless after installing.

---

### Post by lisati on 2008-06-23
You *might* have to tinker with your systems settings to do a restart of your wireless network: more information can be found here: [http://ubuntuforums.org/showpost.php?p=1351902&postcount=2](http://ubuntuforums.org/showpost.php?p=1351902&postcount=2)

---

### Post by westdale on 2008-06-25
I had been able to access Windows XP folders and network devices from Hardy Heron for a number of weeks over my wireless network. 
Something (and I suspect one of the updates in the last week) now prevents it:
Clicking on MSHOME (location shows smb:///) shows nothing; 
WORKGROUP (my NAS drives) does not show up at all; 
I cannot print to my networked laser printer.

FTP share on one of my NAS drives shows up in location network:/// and clicking that item shows the folders in [ftp://192.168.1.21/](ftp://192.168.1.21/) OK.
Bookmarks display the folders OK and direct Samba access works fine in several cases.

I am on wireless at the moment but will try direct connection tomorrow.

---

### Post by jimv on 2008-06-25
OK, I had this exact same problem for quite awhile, but I seem to have fixed it in a rather unexpected way.

I use DD-WRT firmware on my router.  It includes a DNS server.  I turned on the DNS server for my LAN, and gave it a domain (home.local).  After that, my problem with not seeing the shares located on my XP box was solved.  The workgroup is completely browsable now.

Just putting it out there.

EDIT:
I was just thinking about this and was wondering if it's a problem with NetBios support in Ubuntu...like it's not resolving the Netbios names or something.

Try opening /etc/nsswitch.conf and add "wins" to the hosts line, so it should look something like this:

hosts: files dns wins

Then make sure that winbind is installed:

sudo apt-get install winbind

**From:
[http://nawsher.wordpress.com/2008/06/25/resolve-widnows-netbios-hostname-in-ubuntu/](http://nawsher.wordpress.com/2008/06/25/resolve-widnows-netbios-hostname-in-ubuntu/)

---

### Post by westdale on 2008-06-26
Tried reinstall of Samba - as I rather expected, no change (if there is a bug in a recent update, then I have reloaded it!).
Changed from wireless to wired connection. The only change is that the WORKGROUP shows up with Ubuntu machine as only member (no NAS drives).
MSHOME still shows no data -  no access to the windows XP shares.

I have added this to Bug report in Bug #241578

---

