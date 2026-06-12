---
title: "Buttons in applications not working"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by travmanx on 2009-11-10
I noticed this yesterday while in the Ubuntu Software Center, I'd click install/remove and nothing would happen. I thought it was no big deal as I could just as easily do it from the terminal. So I went on thinking it was something to do with Ubuntu Software Center...
I opened up Eclipse (Java Editor) today and noticed that buttons have no functionality to them. I have to do ALT+F or whatever the shortcut is to the button. I thought maybe it was coincindence. However after other attempts with programs, have gotten no such luck.
What has happened?

---

### Post by lavinog on 2009-11-10
Does the problem persist?
Did this happen right after an update?
Do you have desktop effects enabled?
Were the button images change as you clicked on them?

---

### Post by travmanx on 2009-11-10
> **lavinog said:**
> Does the problem persist?
Did this happen right after an update?
Do you have desktop effects enabled?
Were the button images change as you clicked on them?

I disabled a bunch of stuff I did not need like the bluetooth application and printer stuff. Then after a restart, it auto booted right into the terminal (no GUI). I had to do 'sudo aptitude install ubuntu-desktop'.
Edit: When I click button it pushes down and up like it should. Just theres no functionality. 
Buttons like icons for firefox work. It's just the big buttons (sorry I don't know what there called) like the install button in Ubuntu Software Center

---

### Post by lavinog on 2009-11-10
it sounds like you removed a key dependancy.

try to reinstall ubuntu-desktop again, but do a update first
```

sudo aptitude update
sudo aptitude reinstall ubuntu-desktop

```

Does it reinstall the bluetooth stuff that you removed?

---

