---
title: "[SOLVED] Cannot su to root &amp;amp; Error Msg on Updates &amp;amp; Repos"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by lotusalive on 2008-12-12
:confused:

I recently installed x86_64, Encrypted, Ubuntu 8.04 with no W's partition.  _After installing I cannot su to root_, and am _receiving this error msg whenever I attempt to load Synaptic Repositories or install Updates:_

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080422.2)]/dists/hardy/**main**/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080422.2)]/dists/hardy/**restricted**/binary-amd64/Packages.gz  

Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.  (End Msg)

I am not on cdrom, I am installed... So what is this referring to??  Why can't I su to root??

This same 'Repos not loading' error msg was happening with my previous pclos2007 installs, and would not repair via commands, even after remaking partitions and reinstalling 2x.  My first 2 installs of pclos2007 were fine, except that I broke my Syn Pkg Mgr 2x by accidentally loading more than one repository at a time.

Would someone please suggest what might be wrong?  Thanks in advance.

(I posted this last night, but cannot find it in the threads, so am repeating it.)

---

### Post by overdrank on 2008-12-12
Hi and welcome, for info on root sudo you may look here
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
For the errors on the cd rom you will need to remove it from your repos. You can go to system, administration, software sources and uncheck the cd so it will not look for the cd for updates. This link has good info also
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by lotusalive on 2008-12-12
Thanks so much for the speedy reply.  This may be solved.  I'll mark it when I know!

---

### Post by Michael.Godawski on 2008-12-12
Follow Overdrank's suggestions and you should be fine.

Just to be sure please post your sources.list
```

cat /etc/apt/sources.list
```

And here is a little introduction to root and sudo.

[LIST]
[*][http://godawski.oxyhost.com/rootsudo.html](http://godawski.oxyhost.com/rootsudo.html)
[/LIST]

---

### Post by lotusalive on 2008-12-12
I will mark this Solved.  Thank you both so much!

a)  The System>Admin>Software Sources, removing cd-rom, of course worked.  Thank you. 

b)  I don't really understand the root documentation, but you have given me lots to look at, and I'll work on it.  If I have a further question about not being able to get my one terminal, Konsole to allow me to use my p/w for root commands that I can't find, I'll post another thread then.  (This system is so big I feel way over my head!)  

Thanks to both of you for everything above!

---

