---
title: "write permssions in SMB share"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by rtptucks on 2008-05-07
I have just installed Ubuntu to a spare PC which has 2 addtional harddrives for storage, both are formatted with the ext3 file system

initially i had write problems locally on the pc so i changed owernship and write permisons with

sudo chmod -R 0777 /media/disk-1/
sudo chmod -R 0777 /media/disk/

i also made sure i was the correct owner using

sudo chown -R /media/disk-1 /
sudo chown -R /media/disk/

I updated Ubuntu with the lates updates and enabled SMB sharing so my windows system and media centre can see the share on the network.

Viewing the shares seem to be okay but when i write to them from my windows PC sometimes it will write and then after i have succesfully sent some files i will then try and write to another share and it says permission denied, even though i have the set the permission to allow other users to read & write? say if i create a new folder and share i can then write to this but after writing i then get the same error?

I hope somebody has some ideas on how to fix this?

Many thanks in advance.

Wayne

---

### Post by rtptucks on 2008-05-07
someone told me

" oh dont worry if you get problems with Ubuntu, the forums are ace, people reply quick"

i guess either people dont know the fix or these forums are too  busy for people to notice my thread!

Guess ill have to go back to Windows if nobody is able to offer assitance?

---

### Post by jtrindle on 2008-05-07
The forums are good but you're relying on the luck of the draw when it comes to response.  I'd wait at least 2 or 3 days to get an authoritative answer, especially with a non-mainstream thing like sharing Samba volumes.

I don't know what the issue you are facing is, though I've seen it before.  Here are my settings that seem to work fairly well:

in /etc/smb.conf:

[shared]
comment = Linux Shared Files
writeable = yes
locking = yes
path = /opt/shared-samba
public = yes

permissions are 777 as you stated.

Here's a possibility:  Check the actual permissions and owners in the subdirectories you are creating.  In my case, even though the  top level directory was 777, the directories I created under it (via the Samba mount from the windows machine) were 755 and owned by the user I logged in as!

You may need to add

   create mask = 0666
   directory mask = 0777

to your settings, but I have NOT TESTED THIS YET, it's just a guess based on the [home] settings.

---

