---
title: "Samba Won't Automount via fstab"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by jlacroix on 2007-08-22
Hello! I have a quick problem regarding automounting a samba share on my fstab.

When I run this command, I get no errors, the folder acts like its mounted, but it's not:
```

sudo smbmount //fileserv01/data /mnt/domaintemp -o username="landaal0\administrator" password=password

```

Basically what I need to accomplish is to automount the share "//fileserv01/data" which requires the username, password and domain in order to connect, and then I need to have full write access to all users. I just need something to try in a terminal and if it works I would then need to know what to type in fstab.

Thanks to anyone that can help me solve this frustrating problem. I'm usually very good with fstab when it comes to mounting local hard drives, but samba for some reason hates me.

---

### Post by livestockPimp on 2007-08-22
//server/folder        /mnt/windows        smb     username=administrator,password=pass123,fmask=0777,dmask=0777 1 2

That is what I use successfully to connect windows share to a linux machine in fstab.

---

### Post by jlacroix on 2007-08-22
When I try it that way, I'm getting an access denied error. This is what I'm using now:
```

//fileserv01/data /mnt/wodata smb username=administrator,domain=landaal0,password=scoobiedo,fmask=0777,dmask=0777 1 2

```
I have to add the domain in there, so I just guessed at putting "domain=landaal0". I'm pretty sure the command doesn't recognize the way I typed in the domain. Perhaps if I can get the domain in the command string properly, it may work?

I searched Google for about an hour or two and couldn't find anything. :(

---

### Post by livestockPimp on 2007-08-22
ah, I have never mounted samba inside a domain,
there are only 2x things I can think of, the smbmount docs specify that you use "user=admin/workgroup" you could try using that method for a domain, either that or would you be able to create a local user account on the machine for the smb shares?

---

### Post by jlacroix on 2007-08-22
It looks like I found it!

Here is what I put in my fstab to fix this issue:
```
//10.1.2.70/data /mnt/wodata cifs rw, domain=landaal0,username=administrator,passwd=password,uid=administrator,gid=root 0 0
```

Thanks for your help!

---

