---
title: "How do i upgrade and keep configurations"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by wlraider70 on 2009-11-04
So EVERYONE has said its best to do a fresh install with a new release.
so i have a small server im working on, and of course i don't want to restart configuring it.

so how do i do a fresh install and still save my configurations?

---

### Post by papangul on 2009-11-04
People like to do fresh installs on desktops, because various audio,video etc related problems might crop up but on server it should be okay to just dist-upgrade.

Personally, I know all configuration files in /etc which I have altered.

---

### Post by nothingspecial on 2009-11-05
What I do is have home on a seperate partition and back up any config file I alter when I alter it to my home. Then you just have to copy them back.

Then I would use this little tip I saw recently
```
dpkg --get-selections > ~/pkgs.lst
```

That will make a list of all the packages you currently have installed on your system. After you`ve installed, simply 
```

sudo apt-get install dselect
sudo dpkg --set-selections < ~/pkgs.lst
sudo apt-get dselect-upgrade
```

That`ll put everything back how it was.

---

### Post by Zoot7 on 2009-11-05
A good idea is to use a separate home partition. There's a nice guide here:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

That way it's just a case of installing Karmic, installing all your applications, and then re-activating your old home partition, and Ubuntu is exactly as you left it, with all your documents and settings.

---

### Post by wlraider70 on 2010-07-15
I'm almost ready to upgrade, I'd like to copy the whole file system to an external, but i get permission denials. 

is there a way around this?

---

### Post by nothingspecial on 2010-07-16
```
gksudo nautilus
```

or just follow the psychocats link, you might have to add a sudo to this command

```

find . -depth -print0 | cpio --null --sparse -pvd /new/
```

so that it becomes


```
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
```

it does mention that a few lines down.

---

