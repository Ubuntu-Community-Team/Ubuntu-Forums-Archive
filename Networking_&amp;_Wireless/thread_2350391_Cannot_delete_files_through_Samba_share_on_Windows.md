---
title: "Cannot delete files through Samba share on Windows host"
date: 2017-01-24
forum: Networking &amp; Wireless
---

### Post by tekumi on 2017-01-24
Hello,

I've recently started using Ubuntu and am kinda new to the whole topic. I set up Ubuntu Server 16.0.4.1 LTS in a Hyper-V machine on a Windows 10 host. I'm running the Symfony PHP-framework on the Ubuntu guest and am trying to implement a network share I created with Samba into my Web development IDE.

My Samba share is configured like this: 
> 
[webdevelopment]
path = /home/tekumi/project
public = yes
writeable = yes
browsable = yes
directory mask = 0777
create mask = 0777
force user = root

And while I can read, change, save and delete files through windows (host) explorer (\\ip-of-ubuntu-guest\webdevelopment), I cannot delet files through the Editor (Atom). I simply opened the network share as a project folder in atom, when trying to delete a file I receive a permission failure.

My questions are:
- does anyone know how I configure samba so that my editor can delete files?
- can anyone recommend an alternative IDE OR whole solution to what I am trying to do? Files should be stored on the Ubuntu guest, development should happen on Windows host without having to manually copy files


Thank you and best regards

---

### Post by justincase2 on 2017-01-25
> **tekumi said:**
> Hello,

I've recently started using Ubuntu and am kinda new to the whole topic. I set up Ubuntu Server 16.0.4.1 LTS in a Hyper-V machine on a Windows 10 host. I'm running the Symfony PHP-framework on the Ubuntu guest and am trying to implement a network share I created with Samba into my Web development IDE.

My Samba share is configured like this: 

And while I can read, change, save and delete files through windows (host) explorer (\\ip-of-ubuntu-guest\webdevelopment), I cannot delet files through the Editor (Atom). I simply opened the network share as a project folder in atom, when trying to delete a file I receive a permission failure.

My questions are:
- does anyone know how I configure samba so that my editor can delete files?
- can anyone recommend an alternative IDE OR whole solution to what I am trying to do? Files should be stored on the Ubuntu guest, development should happen on Windows host without having to manually copy files


Thank you and best regards
If it were me, I think I'd create a second share whose name isn't so long and see if that one works.

[http://www.kixtart.org/forums/ubbthreads.php?ubb=showflat&Number=81647&site_id=1#import](http://www.kixtart.org/forums/ubbthreads.php?ubb=showflat&Number=81647&site_id=1#import)

"[COLOR=#313131][FONT=Verdana]Windows for Workgroups has a NetbIOS limit of 15 characters for computernames and 12 characters for share names[/FONT][/COLOR]"

---

