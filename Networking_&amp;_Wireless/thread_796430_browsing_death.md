---
title: "browsing death"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by M0phead on 2008-05-16
I am a complete newb to ubuntu (or xubuntu gutsy as i am using) and i am completely perplexed by a bizare problem nobody else seems to have.:confused:
I have instaled xubuntu and connected it to my router (an old but functional d-link dsl-g6o4t) by an ethernet cable. 
xubuntu reports that there is a conection via lan, and i can access my routers settings from web browser, but when i try to access any web page, it will not load.
my router also reports that there is a working connection, and the router does seem to be working because the other pc connected to it (windows vista:mad:) is browsing quite happily (that is how i am asking this question).
Does anybody know what is going on?
Can anybody help?

---

### Post by DieB on 2008-05-16
how is your router configured?
is it really configured as router or do u use it as a switch and each computer connects separatly to your ISP?

---

### Post by cdw38 on 2008-05-16
It sounds like your DNS server is not set up correctly.  Try typing:
> host [www.ubuntuforums.org](www.ubuntuforums.org)
in a terminal.  It should almost immediately return an IP address.  If not, go back into the terminal and type:
> sudo emacs /etc/resolv.conf
And add a line (the file might be blank right now, don't worry about that):
> nameserver 192.168.1.1
Where you replace 192.168.1.1 with the address of your router.

Before closing emacs, make sure to save the file by Ctrl-X-S (holding Ctrl and then pressing X and then S - it will say at the bottom "Wrote file /etc/resolv.conf").

Hopefully that works.

---

### Post by M0phead on 2008-05-16
errrr...
i may have mentioned that i am very new to this...
could you explain step by step what i must do?

---

### Post by M0phead on 2008-05-16
i put [www.ubuntufurums.org](www.ubuntufurums.org) into terminal.
it showed an ip adress (not one i recognise)
and also:
;;wrning:message parser reports malformed message packet.
;;connection timed out; no servers could be reached
does this help?

---

### Post by M0phead on 2008-05-16
i put the sudo emacs thing in but it returned:
sudo: emacs: command not found
what does this mean?

---

### Post by cdw38 on 2008-05-16
If you are in a terminal and type "host www.ubuntuforums.org" and get back an IP address, then its not a DNS problem.

Instead of emacs then, just type "sudo mousepad /etc/resolv.conf" and see if there is a nameserver entry.  Emacs is an editor; it says command not found because you don't have it installed.  To install it, type "sudo apt-get install emacs" .

I am far from an expert though so if its not a simple DNS error I don't really know...

---

### Post by M0phead on 2008-05-16
i have just tried mousepad and found the conf file, i entered details and saved but orriginal problems still persist.
any ideas?

---

### Post by M0phead on 2008-05-16
i tried the sudo install emacs command but it returned
E: couldnt find package emacs.

---

### Post by Iowan on 2008-05-16
> **M0phead said:**
> i tried the sudo install emacs command but it returned
E: couldnt find package emacs.
was that ```
sudo install emacs
```or ```
sudo apt-get install emacs
```
Personally, I like **pico** - to each his own.
Could you post (cut/paste) your **/etc/resolv.conf** file?
Also... are you assigning static addresses or using DHCP from the router (or elsewhere)?

---

### Post by M0phead on 2008-05-16
it was sudo apt code,
i cant cut and paste unfortuntunatly cause xubuntu is on different pc

---

### Post by M0phead on 2008-05-16
:confused:any ideas?
:confused:anybody?

---

### Post by M0phead on 2008-05-16
:confused:Help?

---

### Post by ugm6hr on 2008-05-16
> **M0phead said:**
> i put [www.ubuntufurums.org](www.ubuntufurums.org) into terminal.
it showed an ip adress (not one i recognise)
and also:
;;wrning:message parser reports malformed message packet.
;;connection timed out; no servers could be reached
does this help?

Just to double-check:
```
ping ubuntuforums.org
```

This should give you the same ip address.

---

### Post by M0phead on 2008-05-17
i have discovered annother strange thing...:confused:
i cannot access web adresses in firefox,
however,
i can access them by puting ip adress instead of web adress into browser.
*as a note i am finding ip adresses using "host" command in terminal.


Does this help?

---

### Post by M0phead on 2008-05-17
also, in reply to question, when i use ping command it does return same ip.
also, can i stress again how i am a complete newb to xubuntu so if there is any simple thing that no competant user of xubuntu would have overlooked, i probably have.


Does this help?

---

### Post by M0phead on 2008-05-17
Is it also worth mentioning that i had this same problem on privious (and first) install of xubuntu.
It was daper drake and i installed gutsy to hopefully rid myself of the problem... evidently it didnt work.

---

### Post by M0phead on 2008-05-17
also it was not connected to the internet when i did install.

---

### Post by ugm6hr on 2008-05-17
Not being connected at the time of installation should not affect browsing - only updates.

To enable all repositories (for updates etc) - follow the link in my signature (Repos).

It seems like Xubuntu can resolve DNS, but Firefox cannot.  I have never encountered this before.

Perhaps an ipv6 issue with Firefox...  Maybe someone with more knowledge than me can confirm that this is a possibility.

---

### Post by M0phead on 2008-05-17
Any more help would be very welcome, i have no more ideas myself...

---

### Post by ugm6hr on 2008-05-17
> **M0phead said:**
> Any more help would be very welcome, i have no more ideas myself...

I don't know if this will work, but it is easily reversible, and worth a try:
[http://en.opensuse.org/Disable_IPv6_for_Firefoxhttp://en.opensuse.org/Disable_IPv6_for_Firefox](http://en.opensuse.org/Disable_IPv6_for_Firefoxhttp://en.opensuse.org/Disable_IPv6_for_Firefox)

---

### Post by M0phead on 2008-05-17
i  cant follow link, internet is messed up...

also, i found more strange stuff.
I can view this page in xubuntu but i cant sign in, it just seems to forget me.

---

### Post by M0phead on 2008-05-17
It worked!!!:):):):):):lolflag::KS
thank you so much,
one final question:
how do i flag this as resolved?

---

### Post by M0phead on 2008-05-17
actually, never mind.:)

---

### Post by M0phead on 2008-05-17
hey im back cause although firefox is working perfectly,
sympatic is experiencing the same problems as firefox used to...
is there an ipv setting i can change on that?

---

### Post by ugm6hr on 2008-05-17
> **M0phead said:**
> hey im back cause although firefox is working perfectly,
sympatic is experiencing the same problems as firefox used to...
is there an ipv setting i can change on that?

Make sure you have enabled all repos - see the link below.

You can disable ipv6 in Gnome - I will try and find the link for you.  However, I still can't understand why Terminal works (with ipv6), but other apps don't :confused:

EDIT: Here's the link: [http://ubuntuforums.org/showthread.php?t=87798&page=14](http://ubuntuforums.org/showthread.php?t=87798&page=14) (Post 131 & 133 have 2 alternative methods - try them both if necessary)

---

### Post by M0phead on 2008-05-17
i have done as recomended in previous post and tried a sudo-apt update.
it has unfortunatly failed (i think), returning:

ben@ben-desktop:~$ sudo apt-get update
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg                             
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg                             
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB           
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_GB               
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_GB                  
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB     
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_GB            
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB       
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_GB              
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB     
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_GB            
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_GB
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_GB
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_GB
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_GB
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_GB
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_GB
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_GB.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_GB.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_GB.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_GB.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_GB.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_GB.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_GB.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_GB.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_GB.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_GB.bz2)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_GB.bz2](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_GB.bz2)  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_GB.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_GB.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_GB.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by M0phead on 2008-05-17
has anyone seen this before?
does it help?

---

### Post by ugm6hr on 2008-05-18
> **M0phead said:**
> has anyone seen this before?
does it help?

I'm afraid I'm not sure now.

Maybe someone else?

This thread is getting really long now - it might be worth starting a new one with a more relevant title about e.g. unable to connect to repo with a summary of the Firefox ipv6 issue.

---

### Post by M0phead on 2008-05-18
ok i will do that. 
btw- thanks escpecialy for all help.

 new thread is :

[http://ubuntuforums.org/showthread.php?p=4985307#post4985307](http://ubuntuforums.org/showthread.php?p=4985307#post4985307)

if anybody has any replies, please post them there.

---

### Post by ugm6hr on 2008-05-18
> **M0phead said:**
> ok i will do that. 
btw- thanks escpecialy for all help.

 new thread is :

[http://ubuntuforums.org/showthread.php?p=4985307#post4985307](http://ubuntuforums.org/showthread.php?p=4985307#post4985307)

if anybody has any replies, please post them there.

I've closed this thread now, since the initial browser problem is technically solved.

---

