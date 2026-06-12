---
title: "No more smb access after migration to UBUNTU 20.04 from UBUNTU 19.10"
date: 2020-04-27
forum: Networking &amp; Wireless
---

### Post by lepolau on 2020-04-27
Hello everyone,
I no longer have access to my devices (NAS and other pcs - windows) from Nautilus. The command smb://IP address doesn't work anymore since the upgrade.

I tried to change the parameter "client max protocol = NT1" in client max protocol = NT1 since my NAS is still in smb1 version. But without change, I can't navigate the network using smb, but I can do it with AFP.
I don't know if this will be useful but I also added "/usr/lib/x86_64-linux-gnu/gnome-vfs-2.0/moduleslibsmb.so" and modified 
"/etc/gnome-vfs-2.0/modules/extra-modules.conf" to account for smb in nautilus. I can browse the Windows network again, but I can't access my files, just the share folder.
To get around the problem I went through an fstab mount, it works but it's less convenient and the login is slower.
Hopefully someone will be able to help me.
Thanks in advance.[ATTACH=CONFIG]285635[/ATTACH]

---

### Post by lepolau on 2020-04-28
i open a bug report : [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1875354](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1875354)

---

### Post by Morbius1 on 2020-04-28
> I tried to change the parameter "client max protocol = NT1" in client max protocol = NT1 since my NAS is still in smb1 version.

You have created a paradox.

The version of samba in Ubuntu 20 disables SMB1 ( NT1 ) on the client so it starts with SMB2.1 and goes up to SMB3.X. You can't have a client min at 2.1 and a max at NT1. That's why you got this error message when you ran smbclient:
> protocol negotiation failed: NT_STATUS_CONNECTION_DISCONNECTED

Remove [highlight]client max protocol = NT1[/highlight] and add
```
 client min protocol = NT1
```
And make sure it's in the [global] section - like right under the workgroup = WORKGROUP line not at the end of the file.
Then restart smbd:
```
sudo service smbd restart

```
smbclient should now work so see if Nautilus will.

---

### Post by lepolau on 2020-04-28
I just added "client min protocol=NT1" to my /etc/samba/smb.conf and it works again. Thanks to all of you for your help and sorry, I should have read the official doc instead of some sites.
The problem is solved for me.
Thanks again.

I had to go a bit fast, in fact I do have access to my data, no more error messages but the files are seen as folders.
I can't delete them (a window telling me this is not a folder), or open them (a window telling me this is a folder).

I've just seen that there's a bug report in this sense :[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1872476](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1872476)
I'm gonna go back with a cifs editing in the meantime.

---

### Post by Morbius1 on 2020-05-01
I see from the bug report that a PPA has been created to fix this: [https://launchpad.net/~sergiodj/+archive/ubuntu/samba-bug1872476-v2](https://launchpad.net/~sergiodj/+archive/ubuntu/samba-bug1872476-v2)

I tested this on a server system that I forced to NT1 and it seems to work.

---

### Post by larbac2006 on 2020-05-05
Hi

I'm in the same situation. My NAS only accepts SMB1 protocol.
I have edit the samba.conf, added the PPA that updated samba files, but I still can only see the folders and not the files....

Any other ideas?
Thanks

---

### Post by Morbius1 on 2020-05-05
In my opinion the only logical approach would be a CIFS mount which is Linux Kernel based and doesn't use the samba client or gvfs to make a connection. 

As a template you can use my accepted answer at askubuntu: [https://askubuntu.com/questions/1234934/20-04-upgrade-makes-nas-unavailble](https://askubuntu.com/questions/1234934/20-04-upgrade-makes-nas-unavailble)

 > CIFS is Linux kernel based and knows nothing about smb.conf so making changes there will have no affect on a cifs mount.
  I'm going to assume the NAS is running only SMB1 so you will need to specify that in your fstab declaration by adding vers=1.0 to your list of options:

  ```
//192.168.1.2/share /mnt/FileServer cifs username=guest,uid=1000,vers=1.0 0 0

```  You will probably need to add another option to change the default security mode that SMB1 had in those days: sec=ntlm So the line becomes:

  ```
//192.168.1.2/share /mnt/FileServer cifs username=guest,uid=1000,vers=1.0,sec=ntlm 0 0

```  **EDIT: Reason for adding vers comes from man mount.cifs for the vers option:**  [QUOTE]The  default  since  v4.13.5  is  for the client and server to negotiate the highest possible version greater than or equal to 2.1. In kernels prior to v4.13, the default was 1.0. For kernels between v4.13 and v4.13.5  the  default  is 3.0.

  The Linux kernel in Ubuntu 16.04 was accessing the NAS using  vers=1.0. Now it's trying to access it between 2.1 and 3. Adding  vers=1.0 overrides the default.[/QUOTE]
***EDIT**: For most users I would turn this into an automount by adding [highlight]noauto,x-systemd.automount[/highlight] to the list of options.*

---

### Post by larbac2006 on 2020-05-05
After a reboot of my NAS, everything is back to normal. Finally

---

### Post by i-choose-linux on 2020-05-05
I just have to vent a little bit about this problem.  I have used Linux almost exclusively for 6 years.  Just prior to this I was experimenting with Xubuntu and Ubuntu.  I was running Xubuntu on my main machine and was pretty impressed with it.  Ubuntu with the Gnome desktop was another matter but I kept going back to it trying to see if experience would reveal the logic behind it, but that was not the case.  Anyway, I upgraded to 20.04 and ran into the SMB problem.  I have spent hours researching this.  Finally in desperation I did a few things.  I took Xubuntu off of my main machine and went back to Debian.  I took all the files on my USB attached to my router and moved them to Google Drive.  I am hoping that with the next release Ubuntu will get this straightened out.  It seems to me that the whole purpose of Ubuntu is to provide a way of avoiding these problems for the users.  Maybe the developers just missed this?  Just to get an idea what the situation was with other distros I tried MX Linux, no problem, Manjaro, same problem, Linux Mint, no problem.  It will be interesting to see if Mint gets this right in their next upgrade coming in a few months.  Bill

---

### Post by Morbius1 on 2020-05-05
>  Just to get an idea what the situation was with other distros I tried  MX Linux, no problem, Manjaro, same problem, Linux Mint, no problem.
That actually makes sense. MX uses Samba 4.9 and Mint uses Samba 4.7.6  (both of which are End-of-Life btw ). Manjaro and Ubuntu 20 use Samba 4.11.6/7. The difference is how they handle ( or in the newer case drop ) SMB1 ... but more importantly how gvfs handles it. That is where the issue appears to be. They fixed something that ended up breaking something else and when they tried to fix that something else ... CIFS works fine.

---

### Post by Davethehedgehog on 2020-05-06
I had various problems with networking in earlier problems of UBUNTU. In version 19.04 (I think) the problems were largely resolved. On checking the file /etc/samba/smb.conf I found 3 lines had been added to the Global section:

```
server max protocol = SMB3
server min protocol = CORE
ntlm auth = yes
```

These lines are missing in 20.04. Adding them seems to make the network behave itself!

---

### Post by i-choose-linux on 2020-05-06
Thanks, but unfortunately adding those three lines still results in me getting all files turned to folders.  

Bill

---

### Post by Morbius1 on 2020-05-06
Even after installing the PPA fix?

---

### Post by i-choose-linux on 2020-05-08
Just saw this:  >>Even after installing the PPA fix?

---

### Post by Morbius1 on 2020-05-08
Is that a question?
> **Morbius1 said:**
> I see from the bug report that a PPA has been created to fix this: [https://launchpad.net/~sergiodj/+archive/ubuntu/samba-bug1872476-v2](https://launchpad.net/~sergiodj/+archive/ubuntu/samba-bug1872476-v2)

I tested this on a server system that I forced to NT1 and it seems to work.

---

### Post by i-choose-linux on 2020-05-08
Sorry, bad previous post.  Thanks for the link.  I just took a fast look and I will test it in a few hours.  Bill

---

### Post by i-choose-linux on 2020-05-08
The PPA addition worked.  Big thank you to you and to Sergio.  

As I understand this there were actually two problems.  One was the entries in the smb.conf file and the other a bug in the new release.  

Can you explain to me how you researched this to find the solution?  Also, is it likely that in the next release this whole thing gets fixed?

    Bill

---

### Post by Morbius1 on 2020-05-08
I knew about the newer versions of samba setting min to SMB2 because I religiously read about all changes to Samba - it's just something I do.

The PPA came from the OP's reference to the bug report:
> **lepolau said:**
> I've just seen that there's a bug report in this sense :[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1872476](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1872476)

Normally I look at all bug reports concerning samba ( I don't have a real life ) but this one got away from me. I guess I didn't think many folks would have networked devices that could only speak SMB1.

In my universe I do cifs mounts so none of this had a direct impact on me.

---

### Post by i-choose-linux on 2020-05-08
Thanks again.  Without the community's help many of us and certainly I would not be able to run Linux machines.

BTW, the router where the USB drive was attached is relatively new, a Linksys, purchased in the last 6 months.  When all of this started I checked the firmware and it was up to date.

Bill

---

