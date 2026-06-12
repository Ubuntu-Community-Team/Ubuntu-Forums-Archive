---
title: "Can't write to Samba shares from MS Office apps"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by galileux on 2007-05-10
Actually, I already posted the beginning of this story in another thread, that is:
[http://ubuntuforums.org/showthread.php?t=438456](http://ubuntuforums.org/showthread.php?t=438456)

If I'm doing something wrong, please say so, since I am fairly new in Ubuntuforums...

Getting quite desperate here...

I run a VMware Workstation 6 XP virtual guest under Feisty
When I try to write to the samba share (separate server) I get the following event from Windows:

```
Source: MRxSmb 
Event ID: 50 

Description: 
{Delayed Write Failed} Windows was unable to save all the data for the file \Device\LanmanRedirector.
The data has been lost. This error may be caused by a failure of your computer hardware or network connection.
Please try to save this file elsewhere.
```

Last Data Word in the dump is " ```
c000020c
``` "

It looks like some have resolved the issue by tweaking the **FullDuplex** settings of the NIC
(see  [http://tuketu.com/technology/windows/Windows%20Delayed%20Write.mht](http://tuketu.com/technology/windows/Windows%20Delayed%20Write.mht))

However it didnt work for me, as the NIC in my guest is **VIRTUAL** and it is possible that I need to do something similar on the host's NIC, via Ubuntu.

Any clues? Suggestions? Please...

---

### Post by gonzalov on 2007-05-10
Not sure if this points in the right direction, but I had a similar problem using Win98 in a VMware guest on feisty host.

Is your vmware guest ethernet card "NAT" or "bridged"? I had a "NAT" config and it was messing around good, so I changed to bridged and now I am working perfectly. Bridged will give the guest its own IP.

You can look for this config in the .vmx file of your guest XP; look for the setting:

ethernet0.connectionType = "bridged"

If it says "NAT" try changing to "bridged" (with the VM off) and restart the VM.

BTW, if you have a spare NIC lying around, probably switching NICs could eliminate the possibility of a hardware problem.

Please comment how it goes.

---

### Post by dmizer on 2007-05-10
changing from nat to bridged is a fantastic suggestion here.  if that doesn't work, post the contents of /etc/samba/smb.conf from the server you are trying to write to.

---

### Post by galileux on 2007-05-11
Hi Gonzalo and thanks for your help

> Is your vmware guest ethernet card "NAT" or "bridged"?

It has been "bridged" from the beginning. I forgot to mention it.

> BTW, if you have a spare NIC lying around, probably switching NICs could eliminate the possibility of a hardware problem.

I would leave that to the very last resort... it would be quite traumatic to go about upsetting the Feisty/VMware setup right now...

Here is what I tried since the problems started:

- Tried all the workarounds suggested in MS KB articles responding to the "**c000020c**" keyword search
- Tried to force the vitual network adaptor to 100Mbps
- Tried to swap network cables in case there was one defective

None of the above has worked. Still can't write from Office to the Samba share, while an identical (non-VMware) XP client communicates with the same server with no problems at all....

Hi Dmizer! Thanks a lot for trying to help out!

> If that doesn't work, post the contents of /etc/samba/smb.conf from the server you are trying to write to.

Here is the smb.conf from the server:

```
#
# Configuration file for the Samba suite from http://www.howtoforge.com/samba_setup_ubuntu_5.10_p4.
#
#
#

[global]
   workgroup = CIUSSIGROUP
   netbios name = callisto
   server string = %h
   
   passdb backend = tdbsam
   security = user
   username map = /etc/samba/smbusers
   name resolve order = wins bcast hosts
   domain logons = yes
   preferred master = yes
   wins support = yes
   
   # Set CUPS for printing
   printcap name = CUPS
   printing = CUPS
   
   # Default logon
   logon drive = X:
   # logon script = scripts/logon.bat
   logon path = \\server1\profile\%U


   # Useradd scripts
   add user script = /usr/sbin/useradd -m %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usermod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000


   # sync smb passwords with linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
   passwd chat debug = yes
   unix password sync = yes
   
   # set the loglevel
   log level = 3


[homes]
   comment = Home
   valid users = %S
   read only = no
   browsable = no


[printers]
   comment = All Printers
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   browsable = no


[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   admin users = Administrator
   valid users = %U
   read only = no


[profile]
   comment = User profiles
   path = /home/samba/profiles
   valid users = %U
   create mode = 0600
   directory mode = 0700
   writable = yes
   browsable = no

[hda1]
  comment = hda1
  path = /home/shares/hda1
  valid users = @users
  force group = users
  create mask = 0660
  directory mask = 0771
  writable = yes

[hdb1]
  comment = hdb1
  path = /mnt/hdb1
  valid users = @users
  force group = users 
  create mask = 0660
  directory mask = 0771
  writable = yes

[hdc1]
  comment = hdc1
  path = /mnt/hdc1
  valid users = @users
  force group = users 
  create mask = 0660
  directory mask = 0771
  writable = yes

[USB]
  comment = USB
  path = /mnt/USB
  valid users = @users
  write list = @users
  force group = users 
  create mask = 0660
  directory mask = 0771
  writable = yes
```

Thanks for your help.... the saga continues...

---

### Post by dmizer on 2007-05-12
found your trouble:

```
   security = user
```
this is an essential option if you ask me, but it does require some doing to get it to work under vmware for some reason.

first ... make sure that your windows virtual machine is listed under the same workgroup (CIUSSIGROUP).  it will not work unless your virtual machine workgroup and server workgroup match. (right click "my computer", and select the "computer name" tab).

next ... make sure that your virtual machine is logged in as an actual user account (iow: not administrator, and not guest), and make sure the user account has a password.  insure that the virtual machine user and password are added to the users group on your server.

finally ... map the drive rather than trying to browse to the share via "my network places".  right click on "my computer" and select "map network drive".  under "folder" add this line:
```
//callisto/hda1
```
you can make a network map for each of your shares on your server if you like.

now, when you save a file, don't browse to "my network places" to save it.  browse to "my computer" and use the mapped network drive instead

p.s. you'll get better performance in file transfers by mapping the drive anyway :)

---

### Post by galileux on 2007-05-12
Hi Dmizer

First of all thanks very much for looking at my smb.conf!
Unfortunately though, the problem persists:

> first ... make sure that your windows virtual machine is listed under the same workgroup (CIUSSIGROUP).

It has been so from its creation, and I checked again: the workgroup matches that of the server.

> next ... make sure that your virtual machine is logged in as an actual user account.

The VM uses a user account+ password.
In fact, it uses exactly the same account used by the other XP machine (non-VM) connected to the server (which gives no trouble at all).

> finally ... map the drive rather than trying to browse to the share via "my network places".

This has been done right at the time of the creation of the VM. I always map the network drives in the early steps of XP installation.

I had myself suspected a permission problem and I had tried giving full (777) recursive permissions to the samba directory I was tying to write to.

The fact that the other XP client (same config, same setup, same user) has no problems with the samba shares, plus the fact that the problems **occurs ONLY with apps that create temp files** (like **Office apps**, i.e. **you can save other types of files, like plain text**) makes me suspect that the problem lies in one, or a combination, of the following:

- VMWARE (or its virtual adapter) (it is a beta version - 6)
- UbuntuFeisty_amd64
- The Intel GB-lan card built into the Asus P5B motherboard (works OK from the host OS though).

However, pls do feel free to point out any other problems you may see in the smb.conf file...
If you are interested, I had also posted this thread on the VMWARE Workstation forum, where I received an interesting reply, but found no solution there either, so far:
[http://www.vmware.com/community/thread.jspa?threadID=83952&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=83952&tstart=0)

This is becoming a big problem.
Let me continue to thank you for your kindest support  dmizer!

---

### Post by dmizer on 2007-05-12
is there a reason you need to use vmware's workstation?  you might have more success with vmware server.  i just did some fairly in depth testing with my feisty config and xp pro guest, and i could successfuly write from my guest to my host from ms word (office pro) 2003.

and ... i was able to acomplish this over a wireless nat configured network connection rather than bridged.

so, unless it's not an option for you (for whatever reason), you might simply try a different vmware solution.  in which case i would suggest the server rather than the workstation.

otherwise, you said you have xp sp2 installed.  what version of xp are you using under your guest? language other than english? what version of ms office are you using?  if i can duplicate your problem it would be easier for me to help troubleshoot.

---

### Post by Javaddiction on 2007-05-13
I found your similar thread in the [VMWare forums.]("http://www.vmware.com/community/thread.jspa?messageID=642266")

[COLOR="Red"]**< IGNORE >**[/COLOR]
I can confirm that this issue is also affected when synching an iPod in iTunes with music found on either a samba share with the host or through the vm's shared folders on the host, so i'm not inclined to believe that Samba is at fault.

My only two potential workarounds are either to mount a native partition or mount some kind of other virtual disk on a share. 

I'm not a fan of either of those though. Still looking for a solution as well....
[COLOR="Red"]**< / IGNORE >**[/COLOR]

---

### Post by Javaddiction on 2007-05-13
Disregard my previous post. Apparently my issue is unrelated. I made a samba share set up to look identical to my vmware share and everything seems to be running without a problem. I AM using "security  = share" in my smb preferrences, but so far binding the interfaces doesn't quite work yet.

I don't remember if you mentions this earlier, but have you tried using the VMs shared folders   instead of samba?

---

### Post by galileux on 2007-05-13
Hi javaddiction, thanks for trying to help.
I did not try to use the VM shared folders yet. So far I have been trying to put the VM in a position to operate like the other XP client with the same setup (which has no problems), also connected to the samba server, and I see no reason why it souldn't...

Hi Dmizer, you are very kind.
I did not evaluate VMware Server yet.
I think it doesn't have the same features as Workstation, but I will have a look at it.
If it comes to a crunch, I will have to consider deinstalling Workstation and finding an alternative.

Meanwhile I can tell you that the XP running on both my physical XP client and my VM client is Win XP Professional version 2002, service pack 2, ENUS version.

You can see my hadrware details and my host OS details in the posts above.

As said earlier, on the non-VM client it works flawlessly, while in the VM gives the failed write error with Event ID: 50.

---

### Post by galileux on 2007-05-13
I Dmizer, I forgot to say that Office is Office 2003 Professional EN-US version.

---

### Post by dmizer on 2007-05-13
> **galileux said:**
> 
If it comes to a crunch, I will have to consider deinstalling Workstation and finding an alternative.

you shouldn't have to uninstall workstation to evaluate vmware server.  what's more, the virtual machine you created with vmware workstation should run perfectly under vmware server without having to recreate it.  it should be a quick easy test ... install server, open your already created virtual machine, start it, try to save your document and see if it works.

what this is coming down to at this point is one of three things: hardware, vmware, or feisty.  obviously (if successful) testing with vmware server would point to a possible software problem in workstation.

if you can, you might try opening your virtual machine with a different host too (different version of ubuntu?).  this could be a good test of a possible hardware issue, as well as allow you to eliminate feisty as a possible problem as well.  but i really do doubt that you have a hardware problem.

i'll do some testing later today and see if i can't come up with anything definitive.

---

### Post by galileux on 2007-05-14
Hi Dmizer

I made an incredible discovery today.

When I try to copy files larger than approx 1 MB directly from the Feisty Nautilus desktop to the samba network shares, I receive the following:

```
Error "Timeout reached" while copying "/home/[user][path][name]".
Would you like to continue?

```
So it **looks like the problem lies in the communication between Ubuntu and the Samba fileserver!** Not in VMware!

As stated before, the problem does not occur from the other XP client connected directly to the Samba fileserver.

The problem does not occur when transferring in the opposite direction, i.e. from Samba to the Ubuntu desktop.

The problem looks similar to this other one I found on another forum:
[http://linux.derkeiler.com/Mailing-Lists/RedHat/2006-05/msg00271.html](http://linux.derkeiler.com/Mailing-Lists/RedHat/2006-05/msg00271.html)

Any ideas?

---

### Post by galileux on 2007-05-14
Hi again Dmizer

I found some more info about the issue....
If you have time, take a quick look at this...

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/112794](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/112794)
[http://ubuntuforums.org/showthread.php?p=2618121](http://ubuntuforums.org/showthread.php?p=2618121)

It looks like I am going to have to install the Realtek drivers for my P5B's NIC

I'm not very experienced at kernel rebuilds... any suggestions on how I can get that done without messing up my Feisty setup?

Thanks!

---

### Post by dmizer on 2007-05-14
> **galileux said:**
> Hi Dmizer

I made an incredible discovery today.

When I try to copy files larger than approx 1 MB directly from the Feisty Nautilus desktop to the samba network shares, I receive the following:

```
Error "Timeout reached" while copying "/home/[user][path][name]".
Would you like to continue?

```
So it **looks like the problem lies in the communication between Ubuntu and the Samba fileserver!** Not in VMware!

As stated before, the problem does not occur from the other XP client connected directly to the Samba fileserver.

The problem does not occur when transferring in the opposite direction, i.e. from Samba to the Ubuntu desktop.

The problem looks similar to this other one I found on another forum:
[http://linux.derkeiler.com/Mailing-Lists/RedHat/2006-05/msg00271.html](http://linux.derkeiler.com/Mailing-Lists/RedHat/2006-05/msg00271.html)

Any ideas?

this is an entirely separate issue.  you can solve this issue by taking a look at the second link in my sig.  has nothing to do with the server, it is a failing of nautilus to properly handle samba file transfers.

---

### Post by dmizer on 2007-05-14
> **galileux said:**
> Hi again Dmizer

I found some more info about the issue....
If you have time, take a quick look at this...

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/112794](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/112794)
[http://ubuntuforums.org/showthread.php?p=2618121](http://ubuntuforums.org/showthread.php?p=2618121)

It looks like I am going to have to install the Realtek drivers for my P5B's NIC

I'm not very experienced at kernel rebuilds... any suggestions on how I can get that done without messing up my Feisty setup?

Thanks!

this isn't a "kernel rebuild".  or at least it shouldn't be.  all you have to do is add the realtec driver module.  long gone are the days where you had to rebuild the kernel in order to support a hardware device.

---

### Post by galileux on 2007-05-15
Hello dmizer

I downloaded the tarball from Realtek for the P5B built-in network controller.
I installed the driver but the problem persists.
If I transfer small files from the Feisty client to the Edgy-samba server it's OK.
When I try to transfer larger files, it transfers the first 200k approx, then it gives out the timeout message I posted above.

Do you think the two issues are related? (unability to write large files to the shares both **from the XP VM **and **from the Feisty host**).

Do you think following your tutorial for mounting the samba shares on Feisty, via smbfs, could resolve both issues? If so, That is what I'm going to try next.

---

### Post by galileux on 2007-05-15
Update:

- Realtek driver update did not resolve, so I disabled the P5B's built-in RTL8168b/8111b NIC from BIOS.
- Shoved in an old Realtek 8139 in a PC slot, and adjusted eth0 and MAC address parameters
- Rebooted. Guest now transfers files to Samba shares at the right speed, no errors!
- **HOWEVER** : powered up the XP guest and my heart broke: still get transfer errors from guest to network samba shares, and the same old error if I try to save Office files.

Back to square 1.

---

### Post by dmizer on 2007-05-15
yes ... as long as you're using bridged networking, the share is negotiated independantly.  you could still benefit from my howto though if you decide to take a look.

either way, i still think this might be solved by trying vmware server.

---

### Post by galileux on 2007-05-17
Hi dmizer

its DONE!
The problem was the MTU value for the physical NIC on the host.
The NIC was set by Ubuntu to accept packets of max 1492 units.
The XP guest's virtual adapter was sending packets of 1500 units.
For this reason, traffic from the guest (via the host) to other machines on the network, failed.
I upped the MTU to 1500 on the host and that FIXED IT!

details of the resolutions on this thread:
[http://www.vmware.com/community/thread.jspa?messageID=647773&#647773](http://www.vmware.com/community/thread.jspa?messageID=647773&#647773)

So the problem was two-fold:
on the one hand we had a buggy onboard NIC. That was resolved by actually implementing the early suggestion from Gonzalo: shoving in a spare PCI NIC.

The second part was solved by matching the MTUs between the host's physical NIC card and the XP guest's vitual NIC.

I thank you for your time and for all your help. I just hope this thread will save time to others who may encounter this problem.

I should soon turn to your tutorial to properly set up all the shares on the Ubuntu machine.
Thanks again!

---

### Post by dpro369 on 2007-05-20
well for me i just use konqueror in editing files from my MS doc and save it as it is... with samba installed of course..

---

