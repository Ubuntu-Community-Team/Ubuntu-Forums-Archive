---
title: "cifs: mount error 12 = Cannot allocate memory"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by whoolwerf on 2008-07-25
I have the following setup:

- Vista Ultimate machine for windows media center (using xbox as an extender)
- VMware server 2 (latest beta)
- Ubuntu 8.04 server 32bits as guest on vmware.

On the vista host, I share a directory by normal file sharing. I mount that share on the ubuntu guest, using cifs. fstab line:

//media-center/media  /media-center cifs rw,uid=walto,gid=users,credentials=/etc/media-center.credentials  0 0

When the vista machine boots, I can mount this share and work with it fine.

I use hellanzb on ubuntu to download nzb files. All the downloading is done on the ubuntu filesystem, but the finished files (after par2 and unrar) go to a dir on the windows share, so my media center can pick them up.

When it starts copying the data, after a while, I get "cannot allocate memory" errors. So I unmount the share and try to mount it again: no luck. I get the:

mount error 12 = Cannot allocate memory

I have to restart windows to resolve this. And it goes wrong every time.

I've read on the internet and found about the IRPStackSize in the windows registry. I've created that key and upped to 40 eventually (I was getting desperate), but no change.

sooooo..... Anybody got an idea what's going wrong here? And how I can solve it?

Thanx for helping me think!

Greetings, Walter.

---

### Post by fido on 2009-03-08
I am having the exact same problem and I do mean exactly. Using hellanzb to do my downloading in a VM on 8.04 and transferring the files to windows drives. As soon as my script tries to move the files to windows I get that error. I'm thinking that the solution is different then the one you mentioned because we are using Vista. We are even using the same version of VMWare. I might end up having to go back to Workstation 6.5 and use HGFS shares if I can't get this working.

---

### Post by JustinEdw on 2009-07-26
I am having the same issue but I am using sabnzbd. Has anyone found a solution to this? Mine works fine till it starts transfering files from one machine to another then it looses its connection and is unable to mount again till I restart windows.

---

### Post by DeathWolf on 2009-07-27
Been having the same issue.
Restarting the windows "server" service(samba) usually works.(but sometimes doesnt).
It only seems to happen on large sustained data transfers.

My guess is that it might be vmware's driver fault that's trying to push data too hard(saturating a cpu/core and causing some sort of kernel fault in paging somewhere).(since otherwise large transfers through samba work perfectly fine on my GbE...)

I'd be curious to hear if anyone can find a solution to that issue.

EDIT: in some of the worst cases, you can also manually restart the samba core service:
```
net stop srvnet
net start srvnet
```

---

### Post by aladdinwi@gmail.com on 2009-10-03
I have this same problem with hellanzb and moving the files over to my windows pc, with windows xp pre sp1 there was no problem. with windows xp sp1 and up to vista pre sp1 the HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\LanmanServer
\Parameters\IRPStackSize fix would work. now i am running windows 7 and this does not work anymore i do think it helps some it does not disconnect as often, the weird part is after i get the error errno 12 i can still open my Linux shares with windows and manually move the files over to my windows pc but can't with Linux until i reboot windows than it will work a about a day or two.

---

### Post by Dencrypt on 2009-10-09
I have also tried increasing the IRP stacksize as instructed on several places but this is NOT working on win7 as previous poster noticed.

Restarting samba on windows and remounting on ubuntu usally makes it work again but this is a very bad workaround.

---

### Post by darkkith on 2009-10-23
i have the same issue .. basically i can mount my win7 share... i start untarring a 500meg flie.. and shortly afterwards get a bunch of Cannot open: Cannot allocate memory spam on the screen.  

from that point cannot do anything (ls, cp, etc) on the mounted share.  I can unmount it, but if i try to remount it all i get is cannot allocate memory.

i haven't tried restarting the srvnet service on the win7 box, but if i reboot win7, i can mount and start the problem again.  restarting the service is a very poor solution for a very temporary fix.  basically at that rate i should schedule a job to restart all the services every minute.... 

i've confirmed the HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\LanmanServer\Parameters\IRPStackSize fix doesn't work in win7.

i am not sure if vmware server supports host shares, like workstation does - if that is the case i will try that out and try remember to report back here...  otherwise, any other solutions ?

---

### Post by dmizer on 2009-10-23
> **darkkith said:**
> i have the same issue .. basically i can mount my win7 share... i start untarring a 500meg flie.. and shortly afterwards get a bunch of Cannot open: Cannot allocate memory spam on the screen.  

from that point cannot do anything (ls, cp, etc) on the mounted share.  I can unmount it, but if i try to remount it all i get is cannot allocate memory.

i haven't tried restarting the srvnet service on the win7 box, but if i reboot win7, i can mount and start the problem again.  restarting the service is a very poor solution for a very temporary fix.  basically at that rate i should schedule a job to restart all the services every minute.... 

i've confirmed the HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\LanmanServer\Parameters\IRPStackSize fix doesn't work in win7.

i am not sure if vmware server supports host shares, like workstation does - if that is the case i will try that out and try remember to report back here...  otherwise, any other solutions ?

Is your Ubuntu machine running as a virtual machine on your Win7 box? How much memory do you have allocated to your guest, and is it more than you have available on your host?

---

### Post by darkkith on 2009-10-23
> **dmizer said:**
> Is your Ubuntu machine running as a virtual machine on your Win7 box? How much memory do you have allocated to your guest, and is it more than you have available on your host?

yes i guess i wasn't clear about that.

I am running vmware server 2.0 (latest as per yesterday, i forget the build number).

VM is Ubuntu 9.04.

It has 512meg ram configured to it, host (win7) has 6gb physical ram.  There is 1 other vm running on the host as well, its win7 and has 1gb ram configured to it.

---

### Post by DeathWolf on 2009-10-26
as far as I know this has nothing to do with actual free memory since it happens way before any ram threshold would be hit. However the old irpstacksize did matter but they disabled that setting, so unless we find the equivalent we're probably going to be stuck with only reboot or service restart as "solution"...

I believe this issue is partly caused by mount.cifs doing something the windows server does not expect at all, because however I try with multiple external windows servs&vm, I can not get to get that error with windows guests, only with linux and mount.cifs. I tried changing the rsize/wsize, but to no help.

Maybe moving to smb2 protocol will solve that issue at some point... but I dont think that is near mount.cifs yet...

---

### Post by dmizer on 2009-10-26
What network adapter do you have? I had problems with piping too much traffic through one of my Gigabit cards. I kept having to reboot everything to reaquire my network, so I had to switch to a Realtek Gigabit NIC. Since sending both host and guest traffic through the same NIC effectively doubles the traffic volume, if you've got a flaky NIC, it can cause problems.

My flaky NIC:
```
$ lshw -C network
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: b0
       serial: 00:1e:8c:ca:c4:c8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1 driverversion=2.1.3 firmware=N/A latency=0 module=atl1 multicast=yes
```

---

### Post by darkkith on 2009-11-05
I tried the fix indicated in this page, and it seems to have resolved the issue for me.  I removed the IRPacket regkey from above, and applied this...

[http://alan.lamielle.net/2009/09/03/windows-7-nonpaged-pool-srv-error-2017](http://alan.lamielle.net/2009/09/03/windows-7-nonpaged-pool-srv-error-2017)

basically:

set this to '1'
```
HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management\LargeSystemCache
```

set this to '3'
```
HKLM\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\Size
```

---

### Post by Ogre840 on 2009-11-06
Hello,

I just installed 9.10 Karmic on an older laptop to use as a media PC mainly sharing files from my main Win7 RC box. I finally went through the main issues of getting mostly to my files on Win7, but I am now dealing with the:

mount error(12): Cannot allocate memory

error. On my main computer I was using dual gigabit NICs bridged, but reading some tips on how to get past error 12, I unbridged them.

I'm at my wits end on getting this to work tonight. So far the most help I've found for this problem relate to an older version of Ubuntu, or WinXP (the HKEY trick, which I've now read does not work in Win7) what else am I missing?

Thanks!

---

### Post by bodhi.zazen on 2009-11-07
I am getting this error with my samba server.

The server is Ubuntu 8.04 , client Ubuntu 9.10 and Fedora 11.

> mount -t cifs //server/share /mnt/share/ -o username=me
Password: 
mount error(12): Cannot allocate memory
Refer to the [noparse]mount.cifs(8)[/noparse] manual page (e.g. man mount.cifs)

---

### Post by bodhi.zazen on 2009-11-07
Update:

This ended up being a permissions problem on the server.

Somehow (not sure how) the permissions of my shared directory changed from

rwx

to 

rw

once I fixed the permissions, no more cryptic errors.

---

### Post by Pinzgi on 2009-11-28
Hi,
Since today I do not have access any more to my NAS.
Reading this and other forum entries and trying some described solutions did not help to fix my problem.
 

System environment:
[INDENT]System : Ubuntu 9.10
NAS : WD MyBook Word Edition II
[/INDENT]/etc/fstab:[INDENT]```

//192.168.1.100/public /media/MyBookNAS1 cifs nounix,noserverino,guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
# smbfs mount also does not work
#//192.168.1.100/public   /media/MyBookNAS1          smbfs user,uid=pie,uid=1000,file_mode=0777,dir_mode=0777 0 0

```[/INDENT]when mounting (mount -a) I get the following error:
[INDENT]mount error(12): Cannot allocate memory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)[/INDENT]
I also tried with smbfs (as it worked bevor) but without any success.
Please help me, I'm new in the Ubuntu-World and I need some beginner help :-)

---

### Post by Pinzgi on 2009-11-29
Hi
I found out, that the problem may be my NAS, because I do not get any Web access to it. So I will have to see first what's going on with the NAS.

---

### Post by kaginken on 2010-01-01
DarkKith - thanks!  That reg hack totally did the trick.  

Anyone else having this problem ( cifs mount error 12 = Cannot allocate memory), this is the fix.

FYI - I just installed a CentOS 5.4 server running as a guest inside my freshly installed Windows 7 Pro host OS.  I had that cifs mount problem trying to mount my Windows 7 share from the CentOS server.  problem solved!  Thanks again DarkKith!  :guitar:

---

### Post by cmsdloma on 2010-10-11
I had this exact same problem with the following setup:

Windows 7 Professional machine, joined to a domain called "HOME".
Windows 2003 R2 Server as a Domain Controller, with about 20 user accounts.
Ubuntu v9/KK.

When trying to mount a share from the Win7 machine on the Ubuntu machine, I get the famous "mount error 12 = Cannot allocate memory" error.  However, there is an interesting twist to the story, which I'd like to post on here to help people out.

I have about 20 users registered on the Domain Controller, and the same share from the Win7 box is mounted in each of the user's home folders under /home/userXXX/raid.  Each mount connects with the user's corresponding Domain account and password (saved in a file /home/userXXX/smbuser) and everything works fine.  The share mounted perfectly (after applying the above fix) for all users except Administrator (the global Domain Administrator account).

The mount for the 'root' (which tries to connect to the Win7 box as "Administrator") fails because the username "Administrator" is ambiguous.  The reason for this is that I have an account on the Domain Controller called "Administrator" as well as on the Win7 box with exactly the same username and password.

The solution:  You must qualify the username used to mount the Samba share, when connecting as a Domain user, if its otherwise ambiguous.  So if the Domain is called 'HOME', then specify 'HOME\Administrator' as the user when mounting - or put it in the smbuser file as I did.

If it helps someone, please let me know.  We need to rid the world of this Micro$oft disease!

Cheers,
Dave

---

### Post by flyfishin4trout on 2010-10-18
> **cmsdloma said:**
> I had this exact same problem with the following setup:

Windows 7 Professional machine, joined to a domain called "HOME".
Windows 2003 R2 Server as a Domain Controller, with about 20 user accounts.
Ubuntu v9/KK.

When trying to mount a share from the Win7 machine on the Ubuntu machine, I get the famous "mount error 12 = Cannot allocate memory" error.  However, there is an interesting twist to the story, which I'd like to post on here to help people out.

I have about 20 users registered on the Domain Controller, and the same share from the Win7 box is mounted in each of the user's home folders under /home/userXXX/raid.  Each mount connects with the user's corresponding Domain account and password (saved in a file /home/userXXX/smbuser) and everything works fine.  The share mounted perfectly (after applying the above fix) for all users except Administrator (the global Domain Administrator account).

The mount for the 'root' (which tries to connect to the Win7 box as "Administrator") fails because the username "Administrator" is ambiguous.  The reason for this is that I have an account on the Domain Controller called "Administrator" as well as on the Win7 box with exactly the same username and password.

The solution:  You must qualify the username used to mount the Samba share, when connecting as a Domain user, if its otherwise ambiguous.  So if the Domain is called 'HOME', then specify 'HOME\Administrator' as the user when mounting - or put it in the smbuser file as I did.

If it helps someone, please let me know.  We need to rid the world of this Micro$oft disease!

Cheers,
Dave

You are referring to domain accounts vs local accounts. Im not sure why you even typed the last sentence. If you dont know how windows works then why blame Microsoft. Its been that way since NT.

---

### Post by amidsin on 2010-11-13
I have encountered this problems while trying to mount Windows share from Windows 7 host system to guest Ubuntu Lucid server system in VirtualBox on the same machine.

The suggestion with Windows registry didn't help. I have resolved it based on suggestion from this thread - [http://ubuntuforums.org/showthread.php?t=1439495](http://ubuntuforums.org/showthread.php?t=1439495)

All I had to do is to have proper permissions for a shared folder not only in the sharing options, but on the file-system level as well.

Worked like a charm.:guitar:

---

### Post by amidsin on 2010-11-13
> **amidsin said:**
> I have encountered this problems while trying to mount Windows share from Windows 7 host system to guest Ubuntu Lucid server system in VirtualBox on the same machine.

The suggestion with Windows registry didn't help. I have resolved it based on suggestion from this thread - [http://ubuntuforums.org/showthread.php?t=1439495](http://ubuntuforums.org/showthread.php?t=1439495)

All I had to do is to have proper permissions for a shared folder not only in the sharing options, but on the file-system level as well.

Worked like a charm.:guitar:

Wanted to mention that after I fixed the problem with permissions, I have encountered same error again moving large files to and from the shared folder. At this time the Windows registry hack, which was mentioned for Windows 7 has helped.

Thanks a lot.

---

### Post by garfonzo on 2012-01-04
I thought I would chime in and say that I had the exact problem as the original post stated. I had a Windows 7 64bit machine share mounted on a Ubuntu box. I transferred a large file from the Linux box to the Windows box; this brought down the mounted share on the Linux box. 

I followed the two registry edit and it solved the issue.

---

