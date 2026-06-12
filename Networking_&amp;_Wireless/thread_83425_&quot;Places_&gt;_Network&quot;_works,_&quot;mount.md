---
title: "&quot;Places &gt; Network&quot; works, &quot;mount //server/share&quot; doesn't"
date: 2005-10-28
forum: Networking &amp; Wireless
---

### Post by maphew on 2005-10-28
Hi there,

I have ubuntu 5.04 installed and participating in a windows active directory domain. If I access a windows share via "Places > Network > Servername > Sharename" I get prompted with a login dialog which asks for my username, domain and password, I supply the correct credentials, and we're off to the races. I can access network shares the same as I can from my windows computer and I have the correct permissions (I have write access where I expect to).

Now, how do I get this same access from a mount point so I can use a terminal to write to windows shares?

I've tried "sudo mount -t cifs //server/share /mnt/share -o username=myself" and "sudo mount -t smbfs  //server/share /mnt/share -o username=myself" and both of these allow me to *read* the network shares, but I'm not allowed to *write* to them.

The output from "mount -l" tells me the share is mounted read/write:

//192.168.123.123/data on /media/mattdata type smbfs (rw)


Please help this competent windows user but mostly ignorant linux one get this sorted out. I RTFM all the time, but when it comes to linux there are so darn many I don't know *which* FM is the right FM. :)

Thank you.

---

### Post by Joe_lurker on 2005-10-28
You probably do not have rw to the '/mnt/share' folder.  I like to make my own personal mounting points under '/home/<username>/mnt/share'.  There you can control the permissions.

You should still be able to add files to folders below the '/mnt/share/' mount point, but you will not be able to change the contents of the '/mnt/share' folder.

-Joe

---

### Post by maphew on 2005-10-28
I tried mounting under /mnt, /media and /home/matt/shares with no change. When I look at the owner of  ~/shares when nothing is mounted the owner is matt:matt. After something is mounted it is root:root. However even if I "su" to root, I still can't write to ~/shares.

---

### Post by Joe_lurker on 2005-10-28
Sorry, I missed a point here.  You need to set the suid bit on '/usr/bin/smbmnt' and '/usr/bin/smbumount'.  Use the following commands:

sudo chmod +s /usr/bin/smbmnt
sudo chmod +s /usr/bin/smbumount

Then you will be able to mount the shares as a normal user without using sudo.

-Joe

---

### Post by maphew on 2005-11-01
Thank you for your continued efforts to help this confused person Joe!

 I set the suid bit and when I issue "smbmount /media/matt //server/matt" there is no error reported. However I can't access the mount. "mount -l" says:

none on /media/matt type smbfs (rw)

I tried adding stuff to the smbmnt command line like "-d 777 -f 777 -o username=mydom+myusername" but there is no change in behaviour.

A simple ls -l or  "smbumount /media/matt" takes about  a minute to respond, the former with:

$ ls -l /media/matt
ls: /media/matt: Input/output error

---

### Post by Joe_lurker on 2005-11-01
It looks like the syntax is incorrect for smbmount.  The correct syntax is:

smbmount //<server>/<share> /<mount point>

I assume that this is just a typ-o in your post.  What happens when you run the same command with sudo?

-Joe

---

### Post by maphew on 2005-11-01
yep, there was a typo but not the one you thought. :)  You told me to siud *smbmnt* not *smbmount*, which for some reason appear to be totally different commands using backwards syntax respective to each other. So now I see there are FOUR  (or more??) methods of mounting a windows share, all of which seem to work just enough to make the unwary newcomer think he is attempting to open the correct door. 

In any case, I don't understand why but now when I "smbmount //server/share ~/mntpoint -o username=dom+myname"  I have full read+write access. 

Thank You for your help!

---

### Post by Joe_lurker on 2005-11-01
smbmount calls smbmnt which works through smbfs.  Sort of confusing.  You should be calling smbmount our mount -t smbfs.  smmbount should not be set suid.

-Joe

---

### Post by maphew on 2005-11-01
argh! spoke to soon. I can mount and write to shares on my windows workstation but not to shares from the file servers unless I login as the windows domain admin. So now I'm back to my original question: how can make the connections which seem to always work the way I expect them to in Nautilus also available to terminals?  Am I really just too dumb to understand this or is it actually confusing?

---

### Post by Joe_lurker on 2005-11-02
Try this:

create a file named '.smbcedentials' in your home folder.  This file has two lines:
username = <username>
password = <password>
(replacing <username> and <password> with the appropriate values for your domain).

Create a mount point in your home folder named 'server'

Run the command (all one line replacing <***> with appropriate values):
smbmount //<server>/<share> ~/server -o credentials=~/.smbcredentials

Let me know what happens.  Also could you please post your network info?  It looks like you are trying to connect to a Windows ADS machine and a Windows workstation from Linux?  What version of Windows, etc.

You might want to read these man pages (if you haven't already): smbmount, smbmnt, smbclient.  I believe that Nautilus uses smbclient to connect to the server and transfers files to the temp folder when you open them.

-Joe

---

### Post by maphew on 2005-11-02
why would using a .smbcredentials file be any different from using those same credentials on the command line? In any case today I can logon to the server shares as myself. I have no idea what has changed between now and then. Perhaps I was so tired and frustrated yesterday I managed to mistype my password more than five times in a row? (a light goes on and matt understands the utility of smbcredentials....)

And yes I'm logging into an ADS domain. 

/matt goes off to read a new man page (smbclient)

---

### Post by Joe_lurker on 2005-11-02
If you had any special characters in your password that my have messed up the command line.  In thst case using the credentials file is the only way to make it work.

-Joe

---

