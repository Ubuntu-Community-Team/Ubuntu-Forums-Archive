---
title: "Windows fileshare... Samba maybe doesn't cut it."
date: 2014-12-17
forum: Networking &amp; Wireless
---

### Post by Eirhead on 2014-12-17
I've had this working before, but I forget what I did. Honestly, I think I was using a different package than Samba, but I can't remember for sure.

Anyways, we have a bunch of computers on a national level corporate domain. All I want is a windows fileshare folder that everybody in my local office can connect to. I don't really care if other people in the corporation connect to it either (it's contained within our VPN, and none of the data is that critical, so security isn't an issue). I'm not IT, and we kind of keep this computer off of the IT's radar because they don't like it when we have things connected to the network that they didn't setup or know about.

I notice with samba, I can open up the permissions all the way on the workgroup setting and I can see the folders... but I can't even gain access to browse them (because we're not on a workgroup of course). I have played a little bit with the ADS settings as well with no success. I know when I set it up before, somethings were a bit buggy on the OS, but I managed to have an open permissions windows fileshare without too much configuration and it worked pretty much perfectly. I just can't for the life of me remember what package I installed, or what exactly I did to make it work.

---

### Post by TheFu on 2014-12-20
For CIFS sharing, Samba is the only game - well, that isn't true, there is Alfresco and ZFS, but it is extemely doubtful you used those.  There are many samba guides, especially when zero security is needed.  What have you tried, exactly?  The howtogeek one seems to be easy, but I doubt they use AD.

---

