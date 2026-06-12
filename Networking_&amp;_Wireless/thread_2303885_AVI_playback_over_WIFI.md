---
title: "AVI playback over WIFI"
date: 2015-11-22
forum: Networking &amp; Wireless
---

### Post by mblanco2000 on 2015-11-22
I am trying to upgrade my wireless environment for my LAN.  I installed a Archer C7 router into my network, and everything seems to be going pretty well thus far.  I am testing trying to play an AVI file over wifi from my USB thumb drive plugged into the router, and play that file on my laptop.  I can find and mount the USB drive w/o issue.  When I click on the AVI file to start the playback in the Videos app 3.10.1 I get a pop up message saying, "Could not determine type of stream."

I can play the file back no problem locally, in the same Video app on the same computer.  So I believe that should eliminate the AVI file being a corrupt.  Any help is very appreciated.  Thanks guys.

Sorry in advance if this is not in the proper forum.  I just was not sure where to put it.

---

### Post by SeijiSensei on 2015-11-22
How is the file being distributed by the router? Samba/CIFS? DLNA? NFS?  If you can choose a file-sharing protocol, try NFS.  You'll need to install the nfs-common package on your laptop as well.  See this for details: [https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Client](https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Client)

If that doesn't help, try a different player.  Install the smplayer package and try watching the video with that.

---

### Post by mblanco2000 on 2015-11-22
I have no idea how the files are being distributed from the router. If you mean how I am connecting to the drive I am using Samba, I think.  I connect using smb://192.168.0.1, that would be Samba??  How would I go about checking if not?  So for the very green question here.

I have the drive formated as FAT32 b/c I have multiple laptops/devices accessing the drive.  

I installed an Archer C7 Router AC 1750 to help with wifi speeds on my LAN.  I am still worried about my WIFI LAN speed.  My internet surfing according to Speak Easy is 31.65 Mbps and Up 5.61 Mbps.  However, how do I test my LAN speed specifically?

---

