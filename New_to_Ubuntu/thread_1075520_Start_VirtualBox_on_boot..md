---
title: "Start VirtualBox on boot."
date: 2009-02-20
forum: New to Ubuntu
---

### Post by rgb96 on 2009-02-20
Hey all,

 I need VirtualBox to start on boot, and I know I've seen how to do this like 100 times, but I just can't remember right now.

Ideally, not only would VirtualBox start, but it would start up a specific virtual machine, move it over to the right 1 workspace, and fullscreen it. I'm guessing that would require some shell scripting or something, which I have no experience in. 

However, I could settle for just getting it to run on boot. 

Thanks in advance

---

### Post by somethingkindawierd on 2009-02-20
You could, at the very least, add it to your Sessions preferences. Go to System->Preferences->Sessions and add it as a startup item. This will not boot a specific virtual machine, but it at least get's Virtual Box running.

I believe the command you would enter into the "Command" field is quite simply:
```
VirtualBox
```

---

### Post by rgb96 on 2009-02-20
Anybody? I thought this was pretty easy.

---

### Post by rgb96 on 2009-02-20
Oh thanks. That's what I was looking for.

---

### Post by konqueror7 on 2009-02-20
add this as a session
```
VBoxManage startvm "VM Name"
```

---

### Post by jahilton2002 on 2011-06-09
yes i know back to the future, or in this case past...... this works great...... what do i need to add to terminal to make it fullscreen.

---

### Post by s.fox on 2011-06-09
Thread Necromancy.  Thread Closed.

---

