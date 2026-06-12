---
title: "How to stop a proccess from loading on boot"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by autogun on 2008-12-18
Hello guys,

I've installed nginx web server on my Ubuntu 8.10.
Now, what Im looking for is a way to make nginx NOT to load each time I restart the OS. I want to control the service manualy.

Can you please point me how to do so?

Thanks in advance!

---

### Post by Bölvaður on 2008-12-18
lets begin with the gui way.

Can you disable it from

System &#8594; Prefereces &#8594; Sessions

---

### Post by autogun on 2008-12-18
Thank you for a quick reply, Bölvaður.

Im sorry, I had to point it out that I want to do it CLI'ish..

---

### Post by Bölvaður on 2008-12-18
[http://nixcraft.com/shell-scripting/542-ubuntu-linux-control-startup-services-scripts.html]("http://nixcraft.com/shell-scripting/542-ubuntu-linux-control-startup-services-scripts.html")

---

### Post by donkyhotay on 2008-12-18
You may need to edit you telinit

---

### Post by autogun on 2008-12-18
> **Bölvaður said:**
> [http://nixcraft.com/shell-scripting/542-ubuntu-linux-control-startup-services-scripts.html]("http://nixcraft.com/shell-scripting/542-ubuntu-linux-control-startup-services-scripts.html")

Bölvaður, thanks again!

I've installed sysv-rc-conf and now it's much easier to disable services from booting with the OS.

Screen:
[IMG]http://img56.imageshack.us/img56/5677/sstx9.jpg[/IMG]

Now, what I've done is disabling ngnix 2,3,4,5

The question is, what does those numbers mean?

---

### Post by albinootje on 2008-12-18
> **autogun said:**
> 
Now, what I've done is disabling ngnix 2,3,4,5

The question is, what does those numbers mean?

Those are the runlevels.
See also : man runlevel
Runlevel 0 = halt
Runlevel 6 = reboot
Runlevel 1 = single user mode (or "recovery mode")
Runlevel 2 = the default runlevel in Debian and Ubuntu

---

### Post by autogun on 2008-12-18
Thats all for now, thank you all!

---

### Post by Eto_Demerzel on 2008-12-18
Thanks guys. Exactly what I was looking for.

---

