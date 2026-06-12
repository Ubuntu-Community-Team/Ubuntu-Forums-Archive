---
title: "ssh times out while logging in in 9.10?"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by confused_person on 2009-11-23
Hi there,
I'm using an ipod touch which is not recognized by any programs in Ubuntu, so after extensive searching and with the help of this guide ([https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)) I've determined that the only way to add music to my library is via SSH using an application called dtunes (PwnPlayer was recommended but its developer is on hiatus so it can't be obtained).  Anyway, I finally got the ssh working this afternoon and I was transferring my music just fine. After restarting my computer and re-logging into ssh, however, I keep getting the error "Timed out while logging in". Aside from restarting the computer, I haven't changed anything about my laptop or ipod, so why is this happening? What can I do to fix it? Thank you!

---

### Post by JairunCaloth on 2009-11-23
Sorry, I'm not very fimiliar with ipod touches.

Are you using ssh on the ipod to connect to the computer, or are you using ssh on the computer to connect to the ipod?

---

### Post by confused_person on 2009-11-23
> **JairunCaloth said:**
> Sorry, I'm not very fimiliar with ipod touches.

Are you using ssh on the ipod to connect to the computer, or are you using ssh on the computer to connect to the ipod?

I'm using it on the computer to connect to the ipod.

---

### Post by JairunCaloth on 2009-11-23
Make sure ssh is running on the ipod touch. 
Also double check the IP address you are using to connect to the ipod. If you rebooted it, or turned off wifi and turned it back on, the IP address could change.
Double check what port your ipod expects you to connect on. By default ssh attempts to connect on port 22.

---

### Post by confused_person on 2009-11-23
> **JairunCaloth said:**
> Make sure ssh is running on the ipod touch. 
Also double check the IP address you are using to connect to the ipod. If you rebooted it, or turned off wifi and turned it back on, the IP address could change.
Double check what port your ipod expects you to connect on. By default ssh attempts to connect on port 22.

Haha, the IP address did change. Silly me. But despite entering the new, correct address, I'm still getting the same exact error as before..:confused:

---

### Post by stlsaint on 2009-11-25
you need to add that new ip address to the .ssh known host file.

---

### Post by pi.boy.travis on 2009-11-25
If you have the means, I recommend using Windows in VirtualBox, and syncing your iPod that way.  The open-source tools out there are good, but they don't yet match the functionality of iTunes.

---

