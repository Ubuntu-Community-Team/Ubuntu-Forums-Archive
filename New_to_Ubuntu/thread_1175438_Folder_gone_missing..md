---
title: "Folder gone missing."
date: 2009-06-01
forum: New to Ubuntu
---

### Post by sdqali on 2009-06-01
I moved to Ubuntu 8.04 from XP last week. So far the experience has been good.
But yesterday, i noticed that one of the folders in an NTFS partition has gone missing. It has a lot of personal stuff including photos,. videos etc.
I tried looking for Hidden files in nautilus, but it didnt help. 
What could be the problem ? Is there any way to recover it ?

---

### Post by billgoldberg on 2009-06-01
> **sdqali said:**
> I moved to Ubuntu 8.04 from XP last week. So far the experience has been good.
But yesterday, i noticed that one of the folders in an NTFS partition has gone missing. It has a lot of personal stuff including photos,. videos etc.
I tried looking for Hidden files in nautilus, but it didnt help. 
What could be the problem ? Is there any way to recover it ?

Stuff just doesn't disappear by itself.

NTFS file recovery is possible, google is your friend

---

### Post by rcayea on 2009-06-01
> **sdqali said:**
> I moved to Ubuntu 8.04 from XP last week. So far the experience has been good.
But yesterday, i noticed that one of the folders in an NTFS partition has gone missing. It has a lot of personal stuff including photos,. videos etc.
I tried looking for Hidden files in nautilus, but it didnt help. 
What could be the problem ? Is there any way to recover it ?

I would like to help so I need a few more details. You say you moved from XP to Ubuntu. Does that mean you did a clean install of ubuntu over XP as in you supposedly wiped out XP when you formatted for the ubuntu install? Does it mean you now dual-boot? Please explain.

Thanks,
Randy

---

### Post by HereInOz on 2009-06-01
But you may have to do the recovery of the deleted folder in Windows.  

Before you do, make sure that you have not dragged and dropped it into another folder by mistake.  

This is the usual way that folders "disappear".

---

### Post by sdqali on 2009-06-01
> I would like to help so I need a few more details. You say you moved from XP to Ubuntu. Does that mean you did a clean install of ubuntu over XP as in you supposedly wiped out XP when you formatted for the ubuntu install? Does it mean you now dual-boot? Please explain.

I installed ubuntu in a partition different from that of XP. I did have dual boot for two days and then I began to really like ubuntu and formatted the partition that had XP. 
Thanks for any help !

---

### Post by Daveski on 2009-06-01
> **sdqali said:**
> I installed ubuntu in a partition different from that of XP. I did have dual boot for two days and then I began to really like ubuntu and formatted the partition that had XP. 

You didn't format the same NTFS partition where your personal stuff has gone missing from did you?

---

### Post by eeeandrew on 2009-06-01
If you reformatted the partition which had the folder on it then chances are its gone. It is still possible(in theory) to recover this assuming it wasn't overwritten. I'm not sure what the tools are to do this but modern hard drives can be recovered having been set on fire. 

However, if u completely reformatted it and then installed something over it then the magnetic traces on the hard drive will have been replaced with new ones(the newly installed stuff) in which case its almost impossible to recover it.

It is always advisable to use three partitions for an ubuntu install. The root(/) partition for all the system files, the home partition for your personal files and a swap partition. Using this set up you can overwrite the operating system on the root partition and your settings will be applied to the new install and your documents will be safe. 

It is also advisable to back up any vitally important or sentimentally valuable data to USB stick or other media.

Hope this helps,
Andrew

---

### Post by sdqali on 2009-06-01
> You didn't format the same NTFS partition where your personal stuff has gone missing from did you?
Certainly NOT !
I can access all other folders/files in the partition inquestion except this folder and its contents. 
I can try to recover it by connecting after connecting my HDD to another computer running Windows, but I want to if there is anyway I can do that from ubuntu.

---

### Post by eeeandrew on 2009-06-01
thats good news! Try searching for "system restore" in windows That includes document recovery tools. 

Good luck,
Andrew

---

### Post by Diabolis on 2009-06-01
Also do not write anything on that drive if you are sure your folder is supposed to be there. It is important to not write anything there because in case you deleted it by accident, the new data won't overwrite that section. There is no way to tell if the new data will do this or not, but it can happen. This is needed to use tools like TestDisk.

---

### Post by rcayea on 2009-06-01
> **rcayea said:**
> I would like to help so I need a few more details. You say you moved from XP to Ubuntu. Does that mean you did a clean install of ubuntu over XP as in you supposedly wiped out XP when you formatted for the ubuntu install? Does it mean you now dual-boot? Please explain.

Thanks,
Randy

Could it be a permissions to access anything issue? 

Could it be a security feature that might be set wrong? Check both OS. 

I will do some searching and see what I come up with.

---

### Post by rcayea on 2009-06-01
Did you check to be sure that you reshared any folders if you renamed them?

---

### Post by LewRockwell on 2009-06-01
> **sdqali said:**
> I moved to Ubuntu 8.04 from XP last week. So far the experience has been good.
But yesterday, i noticed that one of the folders in an NTFS partition has gone missing. It has a lot of personal stuff including photos,. videos etc.
I tried looking for Hidden files in nautilus, but it didnt help. 
What could be the problem ? Is there any way to recover it ?

I think there was a virus going around that would just delete all your specific user files, folders, and settings.

that might be a possibility.

---

### Post by sdqali on 2009-06-04
Thank you all for the help.
I could not figure out the reason for the problem. But I managed to recover the images using Photorec and some of the videos using a Windows application, after connecting my HDD to a friends XP system.

Thank You, once again

---

