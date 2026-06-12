---
title: "Some Networking Questions"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by uncle hammy on 2008-08-09
Hi everyone,

I am still in the midst of trying to "de-windowizing" myself.  I am progressing into some of the more complex areas I need to deal with to make this migration to Ubuntu work, and I have a couple networking issues I am hoping someone can help me with...

#1.  VPN connection...  
I installd the vpn connection manager, and I was able to create and connect to my vpn at work.  I can ping all my servers at work, nslookup does 2 way resolution for me, I can even use rdesktop to log into my servers at work (really the most important thing).  However, I can not for the life of me figure out how to browse to my various server shares when my vpn connection is established.

#2.  Local workgroup...
My current setup in my house consists of this ubuntu desktop (currently dual booting with windows vista), a Mythbuntu backend/frontend machine, and a Mythbuntu frontend machine.  When I set up the Mythbuntu machines way back when, I created windows shares, and set the windows workgroup setting in the confguration to match my Vista workgroup. However, now that I am running Ubuntu on my desktop, if I go to Places>Network the only thing I see listed is "Windows Network", which leads me to my Windows workgroup and the shares I set up on those Mythbutnu installations.

I also setup NFS shares on those machines, so why don't I see a "Ubuntu workgroup", listing those shares. How do I create a "Ubuntu" workgroup, so I can completely ditch the windows stuff?

Well, those are my 2 issues (currently :)).  Any help is much appreciated!

Thanks,
Scott

---

### Post by Master Chief on 2008-08-09
Sound like a configuration error, but that is almost impossible to tell without knowing what you did.

Did you install portmap and nfs-common on the client?

```
sudo apt-get install portmap nfs-common
```

Are you mounting at boot using /etc/fstab or manually?

Did you open any ports (firewall) for NFS?

---

### Post by uncle hammy on 2008-08-09
I haven't done anything other than what was done during the default installation of Hardy.  My Mythbuntu installations are going on about 6 months old now, and they were default installation as well.  All I did to them was set up 4 shares (2 smb, 2 nfs mirroring each other), from SYSTEM>NETWORK SHARES, and set the workgroup attribute in smb.conf to the same as my workgroup setting in windows for both machines.

nfs-common and portmap were not installed on this desktop (they were already on the Mythbuntu machines), and now are.  However, after doing this, I still cannot see amything in Places>Network other than the windows workgroup.

I had kind of just assumed that Ubuntu would see other Ubuntu machines and list them, and their shares for me.

As far as mounting, again, I have not changed anything.  fstab sits exactly like it was after the installation.  Do I actually have to mess around with mounting to set up a simple ubuntu workgroup?

---

### Post by uncle hammy on 2008-08-09
OK, an update :)

I installed samba on the new Ubuntu machine, and set smb.conf workgroup to the same as eevrything else and rebooted.  Bingo, Places>Network lists all the machines in my network AND a seperate workgroup with the name that I've set in smb.conf.  So, I'm assuming if I ditch the workgroup attribute out of smb.conf, I'll only show the workstations alone, becuase there is no "workgroup"?  So I think I'm cool with this.

As for my first one, about browsing my work servers via my vpn connection.  After I installed samba, I am able to enter smb://server_name into network borwser, and it goes to it.  However, something is still funky, because it doesn't list all the shares on that server.  I have to actually know the share name, and then I can see my files....

smb://work_file_server_via_vpn = blank screen (though no "can't find" error, which is good)

smb://work_file_server_via_vpn/my_files_share = all files in that share.

Any ideas why just browsing the server wouldn't display the shares available?

Thanks,
Scott

---

