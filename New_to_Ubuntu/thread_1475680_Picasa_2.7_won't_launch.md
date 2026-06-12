---
title: "Picasa 2.7 won't launch"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by 2CV67 on 2010-05-07
Hi guys!

I just installed Picasa 2.7 via Synaptic Package Manager, using the procedure I found [here]("http://www.google.com/linuxrepositories/ubuntu704.html").

Everything seemed to flow as expected & I have Picasa icons in my Applications>Graphics menu.

But when I click on them, nothing happens - not even the little clock or any message.

If I try "picasa" in terminal, I get:
> :~$ picasa
/usr/bin/picasa: line 139:  3369 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: line 175:  3472 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\
:~$ 

I did not separately install Wine - neither Picasa nor Synaptic asked me to.

Any ideas?

Thanks!

---

### Post by Doug11 on 2010-05-07
uninstall it and try Picasa3 straight from google. It works great for me.

---

### Post by 2CV67 on 2010-05-07
I tried "picasa" in a Root Terminal & that works!

So...?

---

### Post by 2CV67 on 2010-05-07
If I launch Picasa via a Root terminal, that then puts an icon on the panel (right hand side) which allows me to launch Picasa "normally", but it disappears after each reboot.
The icon in Applications>Graphics never works.

I can't see any way to define myself as a user for Picasa.

Ideas?

---

### Post by 2CV67 on 2010-05-12
Tried all sorts of things, including Google-Labs-Picasa-for-Linux discussion group, but no success.

Just removed Picasa 2.7 & installed Picasa 3.0 via SynApt.

Works OK immediately...

---

