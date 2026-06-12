---
title: "Can't network 13.10 box to 14.04 wirelessly, only 1 way wired."
date: 2014-05-11
forum: Networking &amp; Wireless
---

### Post by beaucoder2 on 2014-05-11
Hello Ubuntu!

New 14.04 install can't see 13.10 older unit either way wirelessly. Can ping from the 14.04 to the 13.10 but not vice versa. 

Both computers wirelessly connect to the internet without any issues. The 14.04 wireless works with 3 different adapters.

Tried sharing the user folders on each unit. They see themselves on 'Browse Network' but not the other. 

Before I tried (and installed Samba) I wired up the two routers each box uses to each unit. 13.10 is wired to 13.10 router which is wired to the broadband wireless modem. The 14.04 router is wired to the 13.10 router. When the 14.04 unit was wired to the 14.04 router, I could (after a long wait) see the 13.10 user folder (home). But NOT the other way around.

The goal: network both computers wirelessly. One is at one end of the house, the other at the other. Eventually, the 14.04 will be across the hall and down a good ways (about 75 feet.)

Read up on SSH, OPENSSH, Putty, Samba, Gadmin-Samba, NFS and a few others. Gets a bit confusing. 

One odd iterm: When setting the 14.04 home folder to shared, 14.04 got stuck on trying to install libpam-smbpass. Had to cancel. Then did sudo apt-get install libpam-smbpass. Upon reloading the lib activated and showed a brief new user setting. Too brief to see all the details.

To make your efforts easier, if you can point me to the 14.04 best-way-to-do-this link, tutorial or instructions I will gladly do the homework. For testing and trials, the 14.04 is a fresh unaltered install on an SSD drive. Currently it's set as described above with Samba via setting up the shares as is the 13.10. Be glad to redo any way you like. Not so with the 13.10. It is my legacy machine with scads of data, music and programming stuff on it. 

Your suggestions are most welcome. Glad to supply any test data: lspci, ifconfig, iwconfig, etc. 

Ken Wagner
Sugar Creek, Missouri
Where life is sweet, mostly.

---

### Post by beaucoder2 on 2014-05-12
Hello Ubuntu:   Made some progress.  I had changed my /etc/hosts file: shortened my hostname from 16 to 3. BUT, I did not also change the /etc/hostname file entry. Discovered this via an "...unable to resolve hostname..." error message in the terminal. After many fruitless searches I came across an oblique reference to max. name length for a Samba entry of 15. Aha!

The hostname on my 13.10 machine was 16 characters long. It is now 13. Hooray!! Via a wired connection from the 13.10 router directly to the 14.04 unit, I finally had a connection from the 14.04 via Nautilus to the 13.10 home folder. BUT (Arrrrghhh!!!) as soon as I disconnected the cable at the 14.04 machine and connected the wireless adapter to the 13.10 router.....guess WHAT!!!??  The 13.10 can see the 14.04 wirelessly (although the first time takes a while). The 14.04 still cannot see the 13.10 via Nautilus even though the share shows up properly in the 14.04 Nautilus 'Browse Network' window under WorkGroups. BUT when I click on the 13.10 share --- Nothing!!  Screen stays blank and no error message. Immediately after the click on the share, there is a 'Loading...' msg at the bottom right of the screen. Then nothing.

So, some progress but still short of the goal: Connecting a 13.10 computer to a 14.04 computer wirelessly. 

Thanks

Ken

---

### Post by beaucoder2 on 2014-05-12
Shazzam!!!  

This is amazing!!  Re-reading my first post triggered a suspicion.....since the 14.04 had hung up after clicking on the "Install" button during the on-screen Samba setup and then asked for the libpam-smbpass module......ya think????

Sure and begorrah!!  I checked the 13.10 system. NO libpam-smbpass!!  Installed same. Re-booted. Voila!! Wireless networking. 

Some thoughts:
  1. Why doesn't Ubuntu install libpam-smbpass along with Samba as it synchronizes the Unix and Samba password db's?
      Seems odd to leave it out.
  2. Why the lack of error messages?  Hostname too long. Missing libpam-smbpass module. And so on. 
  3. Why not a quick scan utility to show all network stations/printers and maybe some cautions, warnings? 
      The initial load for the Network browsing and scanning takes quite a while. 'smbtree' helps somewhat but more info is
      needed. 

In any case, thanks for being here. Had I not posted and thought carefully about what might be going on.....let's not go there.

I hope this helps someone else out.

Happy patching and fixing!!

Ken Wagner
Sugar Creek, Missouri
Where life is sweet, mostly.

---

