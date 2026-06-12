---
title: "samba mount not always active"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by ramdez on 2007-09-15
Hello all, I have had this issue through Dapper and now Fiesty with the same results. I have a dapper  samba server sharing 2 directories, apps and media.  I have them mounted from a vista machine fine and my dapper (now fiesty) machine and the issue has persisted through upgrades.

I had mounted my remote shares to /network/myshares and now /home/me/myshares with the same results.  I reboot my machine and my shares are not mounted, i try to access the dir and my machine hangs.   i try

sudo mount -a
Could not resolve mount point /home/me/network/media
Could not resolve mount point /home/me/network/apps

i try

sudo invoke-rc.d samba restart gives
root      6374  0.0  0.2  72564  2352 ?        Ss   12:38   0:00 /usr/sbin/smbd -D
root      6377  0.0  0.1  72564  1120 ?        S    12:38   0:00 /usr/sbin/smbd -D

I do sudo invoke-rc.d samba restart same results 

root      6374  0.0  0.2  72564  2352 ?        Ss   12:38   0:00 /usr/sbin/smbd -D
root      6377  0.0  0.1  72564  1120 ?        S    12:38   0:00 /usr/sbin/smbd -D

i gathered these tests through ubuntu forums but aren't exactly sure how to interpret them.  many times a reboot will fix or another mount -a will fix but then later my shares are not active.

I CAN however recreate my local mapping perhaps /home/me/network/new_dir and mount -a and it works...  it makes no sense to me.  recreating the share always solves the problem but i don't like this ( have to re index amarok among other things... )

thanks for any assistance!

---

### Post by ramdez on 2007-09-30
woohoo! community is thriving and strong!

---

### Post by ramdez on 2007-10-09
I created the share under /media and all works well.

i've tried 

/network
/mnt
/home/me

same results.. /media seems to be the only place i can mount drive.  

- thanks ramdez!

---

