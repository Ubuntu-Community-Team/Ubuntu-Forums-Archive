---
title: "how to set-up home PC ubuntu edgy to mac home network?"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by mickeythecat on 2006-11-20
There must be a tutorial on this that I cannot find.  I am a new Ubuntu user and am trying to "see" our mac and vice-versa (and be able to copy files back and forth).  Access can even be unrestricted since both machines are internal to the house.  The Mac runs only off a wireless D-Link router which is connected to a cable modem. The PC (which I am on) runs Ubuntu edgy and is connected by a ethernet cable from the D-link router directly to the PC.  Internet and everything works great, just cannot figure out how to set-up this simple network.

I unsucessfully tried proftpd, gproftp and samba from web help searches and nothing seems to work (I am probably not doing those correctly).

Also under:  system/administration/networking/DNS, I ended up deleting the 3 things that were there and did not write them down (while trying something else awhile ago). Any idea what needs to be there? (and what that does).

Any help would be appreciated.

---

### Post by dmizer on 2006-11-20
since mac is linux based, you might be most successful in implimenting a nfs network.

to enable your ubuntu machine, use the 4th link in my sig.

for your mac: [http://www.macobserver.com/tips/hotcocoa/2001/20010723.shtml](http://www.macobserver.com/tips/hotcocoa/2001/20010723.shtml)

edit:
DNS are your domain name servers.  these are automatically aquired and filled every time you connect to the internet.  there was no harm done in deleting these three items.

edit2:
i just realized i linked you to a mac howto that contained directions for using a non-free shareware program.  you don't have to purchase the program to use it's full functionality (you'll get notifications to purchase on opening), but if you want, you can do some searching in google for "osx nfs" and you should come up with some cli instructions that will perform the same function for free.

---

### Post by mickeythecat on 2006-11-21
Still cannot get this to work.  Here is what I did.  I tried your link: 
[http://www.ubuntuforums.org/showthread.php?t=249889](http://www.ubuntuforums.org/showthread.php?t=249889)

I followed those instructions up to "Mounting Manually" (Steps 1 - 3 below) since for now I would be happy with the mac being able to see the ubuntu linux machine I am on.

1.  sudo apt-get install nfs-kernel-server nfs-common portmap
When configuring portmap do =not= bind loopback. If you do you can either edit /etc/default/portmap by hand or run:
sudo dpkg-reconfigure portmap
sudo /etc/init.d/portmap restart

2.   Editing /etc/exports and saved
sudo gedit  /etc/exports &
I added only the following line based on on mike3k's comment on 14 Sept 2006.

/home 192.168.0.0/255.255.255.0(rw,async,insecure,all_squash,anonuid =1000,anongid=1000)

I also tried
/files 192.168.1.1/24(rw,no_root_squash,async) per the link instructions but this did not work either (I do not have a /files dir so I was doubtful on this anyway).

sudo /etc/init.d/nfs-kernel-server restart
sudo exportfs -a

3.  Install NFS client support
sudo apt-get install portmap nfs-common
 - end of linux ubuntu things - 

On the mac, I did the following.
4.  Downloaded the shareware program NFS Manager and set root pw
5.  Got stuck on "Add Entry" in NFS Connections menu since I clicked the "select" button next to the "NFS Server:" data entry field (which defaults to localhost).  By hitting the select button, it opens up a menu to pick the server - and my ubuntu linux machine did not appear in the list.  I also tried just leaving localhost in the field, but that did not work either.

By the way under the "Mounting manually" I did not understand the first sentence:
"Example to mount server.mydomain.com:/files to /files. In this example server.mydomain.com is the name of the server containing the nfs share, and files is the name of the share on the nfs server"

What is server.mydomain.com? (the name of the server)  I do not have any .com address. Is this the same as the host name on ubuntu under system/administration / networking / general ?

Any ideas as to why the mac cannot see my ubuntu linux machine?

---

### Post by dmizer on 2006-11-21
my post (4th) in this thread: [http://www.ubuntuforums.org/showthread.php?t=299373](http://www.ubuntuforums.org/showthread.php?t=299373) should clear things up for you.

you'll have to change /files to suit your needs.  the above link will give you the information you need to figure out how to do that.

also note, the directory you want exported from your server needs to have chmod 777 in order to have read and write permissions on your client.  (iow: not your /home/mickeythecat directory).  btw, this "restriction" is not exclusive to nfs.  you'll run into the same issues in samba too.

---

### Post by dannyboy79 on 2006-11-21
i had tried mac osx a while ago and was having trouble sharing between winbloz and mac until I found this great freeware program called sharepoints and sharepointsautomounter. check them out. here is the link to sharepoints home location (you'll find other great software also: [http://hornware.com/](http://hornware.com/)

---

### Post by punx45 on 2006-11-24
so i dont know if you figured everything out yet, but i thought i could offer some additional help if you need it.   i have ubuntu and OS X playing nice at home.   i took some screens of my /etc/exports and my NFS Manager setup screen.  from what i read it seems like you might be having some trouble with the NFS manager on the Mac, i had the most trouble with that too.   NFS was pretty much running out of the box on the host (ubuntu) side for me.

[IMG]http://img65.imageshack.us/img65/1124/picture1cr7.png[/IMG]
[IMG]http://img114.imageshack.us/img114/1667/picture2sc8.png[/IMG]

in case you cant read the contents of /etc/hosts in the image: 
```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/media/mediaserver/ 192.168.1.0/255.255.255.0(rw,async,insecure,all_squash,anonuid=1000,anongid=1000
) 
/etc/exports (END) 

```

to be clear, the /etc/exports file is on the Ubuntu machine (host) i was just viewing it on the Mac through SSH.

some info to connect things together:   

NFS Server is the Ubuntu Host (static IP on the LAN and yes thats important)
NFS share is the literal path of what I am sharing - it is an actual directory on the Ubuntu machine
mount point is where i go to view the shares on the mac.   i have it set up to mount in a directory, in this case, imnt is an alias to network locations and it is located in my home folder.   you can also have it mount directly in the network directory in Finder.

hope this helps connect some dots if you still have questions.

also, after you change your settings in NFS MAnager make sure to click Activate Changes  and then go to Computer > Activate Connections if you still arent getting anything.

oh and someone mentioned that OS X is linux based.. technically it is BSD based.   And im sure someone else could get more specific than that.

---

### Post by mickeythecat on 2006-11-25
Thanks to everyone so far with the excellent info; however I am still not getting this to work - I had given up for awhile after spending some time going through all the of dmizer's posts and links and still not getting this to work.  Then I read the last post, but still no - darn.  My problem is likely multiple problems with the underlying issue that I do not understand what all the options are doing.

On the ubuntu side:
1.  As soon as I try the static IP option, I lose all internet connections.   Should this be happening? - probably not.
2.  Under system/admin/networking (network settings menu), I am confused on the options. I attached to this post screenshots of the 4 tabs (and a screenshot of the system/admin/networking tools) but here is a description:
Connections tab:  wired connection selected
General tab:      host name:  mickey (I entered); domain name (blank)
DNS tab:  DNS servers: 192.168.0.1 (not sure if I typed this or where this came from); Search Domains: hsd1.ca.comcast.net (I know I did not type this)
network settings tab:  There are a number of entries here starting with "fe" and "ff" - there was also one for 127.0.0.1 localhost which I ended up deleting since I think I typed that one in at one time also one for 127.0.1.1 mickey which I also deleted.

For my exports file, here is what I have:
/home/mickeythecat/MUSIC 192.168.0.0/255.255.255.0(rw,async,insecure,all_squash,anonuid=1000,anongid=1000)
Not clear on the anonuid and anongid=1000 options (but you have them also) but at least the 192.168.0.1 seems to be in the range (but as I said, not sure if the 192.168.0.1 is correct other than just being consistent with the DNS server # which I may have typed).

On the mac side,
Your screenshots were helpful.  Main question:  do you have to type in the NFS server name (mickey) and NFS share (/home/mickeythecat/MUSIC) or do you hit the "select" button and choose them?  If you can select them, which I cannot, this would indicate weather or not my ubuntu machine is set up properly.

Finally,  I am wondering how the wireless is affecting things.  For me:
1. cable to wireless router that mac notebook can see.
2. Eternet from wireless router directly to ubuntu machine - thus both see the internet.

Should I disconnect the ethernet from router (that goes to ubuntu) and reconnect it directly to the mac? (I did try this). Does any of the network settings make a difference weather or not wireless routers are involved?

Any more ideas would be helpful - especially if someone could explain the IP addresses, the 192.168 or 127 #'s the "localhost" host name (is it required).  And hopefully why I have 192.168.0.1 and your screenshot had 192.168.1.10)

Thanks in advance. I hate to give up now after spending so much time on this.

---

### Post by punx45 on 2006-12-19
if you havent gotten everything sorted out yet, hope this helps!

it looks like you really aren't sure what is going on with your network settings, which appears to be your biggest problem.   you should search for a guide on configuring network settings manually to be sure you are doing things correctly.   

192.168.0.1 is almost certainly not what you should have set as a DNS server.   if anything, it is the address of your router.   in which case, that would be your default gateway, but not a DNS.   in that case, also, it should not be the setting in your /etc/exports file. 

heres more on my settings and why to hopefully help:

192.168.1.1 - My Router (DHCP set to assign addresses starting at 192.168.1.100)
192.168.1.10 - Desktop aka NFS server (set outside of the DHCP range to avoid conflicts)
192.168.1.1xx - Mac or other computers as assigned by DHCP

so in NFS Manager, i have 192.168.1.10 set because that is the IP address of the NFS server.   i used a literal IP address to avoid complications revolving around local hostname issues (need for local DNS or /etc/hosts files)
and yes i put all those settings in manually.  

as for the line in /etc/exports:
i have 192.168.1.0/255.255.255.0   which from my understanding sets a range of IPs that are allowed access to the server.   so in otherwords, that setting would allow any computer with the IP 192.168.1.x to access the NFS share directory. 


so, to get everything squared away, you need to know a few things:

IP of your router, which should be found in the router's settings 
for configuring you IP manually on your server, you will need to know the IP of said server (your choice), the default gateway (the router IP) and real DNS addresses (should also be displayed in router settings)

---

### Post by bishop1641 on 2007-02-23
Was wondering if you got yourself going Mickey. If you haven't please shoot back a reply, I have been having my os x machine working with my ubuntu box for quite sometime except I use Appletalk. It works fine for me. If you still haven't got it working I will be more than happy to share my config files with you.

---

