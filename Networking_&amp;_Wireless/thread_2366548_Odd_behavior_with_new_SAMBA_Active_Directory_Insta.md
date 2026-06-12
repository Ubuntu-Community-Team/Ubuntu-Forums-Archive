---
title: "Odd behavior with new SAMBA Active Directory Install"
date: 2017-07-19
forum: Networking &amp; Wireless
---

### Post by jdo300 on 2017-07-19
Hello All,

I recently setup a new Samba Active Directory server on an Ubuntu 14.04 LTS test VM using the following resources as my guide:

[https://wiki.samba.org/index.php/Build_Samba_from_Source](https://wiki.samba.org/index.php/Build_Samba_from_Source)
[https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller#Introduction](https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller#Introduction)
[https://jimshaver.net/2014/07/13/setting-up-an-active-directory-domain-controller-using-samba-4-on-ubuntu-14-04/](https://jimshaver.net/2014/07/13/setting-up-an-active-directory-domain-controller-using-samba-4-on-ubuntu-14-04/)
[https://www.youtube.com/watch?v=Rf7Hk8qWt1Q](https://www.youtube.com/watch?v=Rf7Hk8qWt1Q)

I was able to get the server up and running with no functional issues (that I'm currently aware of anyway). But I did notice something odd. When I run the following line (which is used in the tutorials to prove that the samba server is running correctly):

```
smbclient -L localhost -U%
```

This is the output I get in the terminal:

```
Domain=[LOCAL] OS=[] Server=[]

    Sharename       Type      Comment
    ---------       ----      -------
    netlogon        Disk      
    sysvol          Disk      
    IPC$            IPC       IPC Service (Samba 4.6.6)
Domain=[LOCAL] OS=[] Server=[]

    Server               Comment
    ---------            -------

    Workgroup            Master
    ---------            -------
```

The first line that says, ```
Domain=[LOCAL] OS=[] Server=[]
``` should have something in between the square brackets for OS=[] and server[]. From what I see in the tutorial pages, the OS field should say something like, ```
OS=[Unix]
``` and the server field should say, ```
OS=[Samba 4.6.6]
``` As mentioned before, the lack of these values doesn't *appear* to be detrimentally affecting anything at this point, but does anyone know why these parameters would not print out correctly?

Thanks,
Jason O

---

