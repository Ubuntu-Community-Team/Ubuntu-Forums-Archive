---
title: "No shared folders option under Administration menu"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by AceRimmer on 2008-04-26
Hello.  I just did a clean install of 8.04 and when i went to administration to enable shared folders with Samba there is no menu option for that.  Was it moved on 8.04?

---

### Post by UKHacker on 2008-04-26
Bumping this as I would also like to know.

---

### Post by tvphil on 2008-04-27
Just like you, I was surprised to discover "Shared Folders" is no longer in system administration. Here's what the folks at Ubuntu replaced it with. First of all, in system administration>services, shared folders should be checked, if it isn't, check the box. Next, go to any folder in your Home folder or the entire Home folder itself, right click and you'll see the words "sharing options" right below "empty trash" as one of your choices. Click on sharing options and you see what has replaced Shared Folders.Hope this helps!

---

### Post by jazzman8866 on 2008-04-27
but how do you change the network name. it defaults to WORKGROUP. i wanna change it. any idea?

James
:KS:KS:KS:KS:KS

---

### Post by UKHacker on 2008-04-27
> **tvphil said:**
> Just like you, I was surprised to discover "Shared Folders" is no longer in system administration. Here's what the folks at Ubuntu replaced it with. First of all, in system administration>services, shared folders should be checked, if it isn't, check the box. Next, go to any folder in your Home folder or the entire Home folder itself, right click and you'll see the words "sharing options" right below "empty trash" as one of your choices. Click on sharing options and you see what has replaced Shared Folders.Hope this helps!

I have shared folders ticked in the services tab, yet whenever I try to share a folder in my home directory I get the following error:

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error permission denied. You do not have permission to create a usershare. ask your administrator to grant you permissions to create a share.

any ideas?

---

### Post by AceRimmer on 2008-04-27
> **UKHacker said:**
> I have shared folders ticked in the services tab, yet whenever I try to share a folder in my home directory I get the following error:

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error permission denied. You do not have permission to create a usershare. ask your administrator to grant you permissions to create a share.

any ideas?

Same here, and I don't see anything about sharing under the Services menu.  I went to the folder and set it to share but after it downloaded and installed software it told me the same error message.

---

### Post by Monicker on 2008-04-27
> **AceRimmer said:**
> Same here, and I don't see anything about sharing under the Services menu.  I went to the folder and set it to share but after it downloaded and installed software it told me the same error message.

I ran into this same problem.  You have to log out and log back in for the change to take effect.  After that it worked fine for me.

---

### Post by AceRimmer on 2008-04-27
Actually now the entry under services is there for folder sharing now.  And I went and setup the samba password using *sudo smbpasswd -a* and it worked fine, but no folder sharing though.

---

### Post by nix4me on 2008-04-27
This change is disappointing.  Before you had the option to share via samba or nfs, not anymore.  The only choice is samba.  I guess those of us who use NFS have to manually set things up now.  Booooo.

nix4me

---

### Post by JAGGEDSPHERE on 2008-04-27
I had this problem on a nearly vanilla install of HH. A reboot was all I needed to get the share set without any errors.

Does anyone know if the current repo version of Samba addresses the Vista incompatibilities? I heard that the Samba team got the official MS docs on SMB and was wondering if they have made any leeway there...

---

### Post by Monicker on 2008-04-27
> **nix4me said:**
> This change is disappointing.  Before you had the option to share via samba or nfs, not anymore.  The only choice is samba.  I guess those of us who use NFS have to manually set things up now.  Booooo.

nix4me

I was poking around with the Kubuntu 8.04 CD on my son's computer just now. That one DOES still have NFS in the gui for Sharing.

Interesting.

---

### Post by chinmaykamat on 2008-09-21
the old gui is available. its just not on the menu. press Alt+F2 to run command and then just run 

```
shares-admin
```


and u will have ur gui back.

---

