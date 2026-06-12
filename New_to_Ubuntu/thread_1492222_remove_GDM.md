---
title: "remove GDM?"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by jfreak_ on 2010-05-24
I never use the login screen, so i was wondering that if i replace it with a lighter login manager would the boot speed increase?

---

### Post by Brandon Williams on 2010-05-24
Why run a login manager at all if you don't use it? You can simply do this:
```
sudo mv /etc/X11/default-display-manager /etc/X11/default-display-manager.orig
echo "" | sudo tee /etc/X11/default-display-manager
```

By emptying out that file (/etc/X11/default-display-manager), you effectively disabled the graphical login manager. Try that out and see whether it impacts your boot speed. If you ever want to restore the previous config, just:
```
sudo mv /etc/X11/default-display-manager.orig /etc/X11/default-display-manager
```

---

### Post by angry_johnnie on 2010-05-24
you could also install an app like bum (in repositories), and then just disable GDM.

---

### Post by -humanaut- on 2010-05-24
I don't think you'd see any significant differences between GDM and any other login manager. I'd recommend SLiM though as a replacement download it and it will offer to default for you.

---

### Post by jfreak_ on 2010-05-25
> **Brandon Williams said:**
> Why run a login manager at all if you don't use it? You can simply do this:
```
sudo mv /etc/X11/default-display-manager /etc/X11/default-display-manager.orig
echo "" | sudo tee /etc/X11/default-display-manager
```By emptying out that file (/etc/X11/default-display-manager), you effectively disabled the graphical login manager. Try that out and see whether it impacts your boot speed. If you ever want to restore the previous config, just:
```
sudo mv /etc/X11/default-display-manager.orig /etc/X11/default-display-manager
```

nah the bootchart still shows three gdm processes running. 


what was the situation when we are forced to login using a console type environment and then use startx?
Is it when the gdm is not working? In that case can i remove gdm and somehow automate the above process?

---

### Post by jfreak_ on 2010-05-25
hmmm looks like[ this]("http://swiss.ubuntuforums.org/showthread.php?p=7176896") is what i want but there are no instrutions there

---

### Post by Brandon Williams on 2010-05-25
> **jfreak_ said:**
> nah the bootchart still shows three gdm processes running.

The method I indicated is the way that I do exactly what you are trying to do ... disable the login manager. Upstart will still run the gdm startup script, but it will not actually start gdm.

Are you certain that you typed the correct filename when you created the replacement file? If you have no file called /etc/X11/default-display-manager, the upstart script will act as if the system is configured to run gdm. If the file exists and does not contain the value "/usr/sbin/gdm", upstart will exit from the gdm script without doing anything.

---

