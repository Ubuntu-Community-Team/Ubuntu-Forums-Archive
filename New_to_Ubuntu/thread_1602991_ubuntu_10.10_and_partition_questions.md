---
title: "ubuntu 10.10 and partition questions"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by indyeah on 2010-10-22
hi all,
well i recently installed ubuntu 10.10 on my pc.i have 4 hard drive partitions namely C,D,E,F.in C drive i have windows7 and all its apps.i installed 10.10 in my D drive which had some pics and music files already stored there.my question is when i install any apps in my 10.10 like chrome,opera.pidgin etc etc,where does the installation files of these get stored?

secondly,in places i can see desktop,documents,pictues,downloads etc etc if i save any files to these folders they get saved in which of my hard drive???

i am asking these above questions because my C drive has less than 1 GB memory left and i dont want the storage to reduce further.

also i installed my ubuntu within my windows system using wubi.

any help and guidance will be appreciated

---

### Post by Paqman on 2010-10-22
> **indyeah said:**
> hi all,
well i recently installed ubuntu 10.10 on my pc.i have 4 hard drive partitions namely C,D,E,F.in C drive i have windows7 and all its apps.i installed 10.10 in my D drive which had some pics and music files already stored there.my question is when i install any apps in my 10.10 like chrome,opera.pidgin etc etc,where does the installation files of these get stored?


When you use the built-in package management tools like Ubuntu Software Centre or Synaptic, it downloads the .deb files into /var/cache/apt/archives. If it's an app that you've downloaded from a website most browsers will drop the installer into your Downloads folder. Once these apps are installed they'll have created files in various parts of the system, but you don't really need to know where they are. The package manager knows how to remove them properly when you uninstall them.

> secondly,in places i can see desktop,documents,pictues,downloads etc etc if i save any files to these folders they get saved in which of my hard drive???

The same place you install Ubuntu to, which in your case is a virtual partition. From within Ubuntu it'll look like a normal Ubuntu filesystem, but from Windows it'll look like a large file sitting on your D drive. You won't be able to access them from Windows unless you save them to one of the NTFS partitions when you're in Ubuntu.

> i am asking these above questions because my C drive has less than 1 GB memory left and i dont want the storage to reduce further.

If you install Ubuntu onto D, then it can't affect C at all. They're completely separate partitions.

You need to create some more space on C. Filesystems that are very full will experience heavy fragmentation, which will make Windows run like a dog.

---

### Post by indyeah on 2010-10-22
thanks paqman that cleared a lots of doubts in my mind

---

