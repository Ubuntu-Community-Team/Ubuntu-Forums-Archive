---
title: "network detection"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by skt.diaz on 2011-02-27
i use my nokia e71 to connect to d internet. ubuntu doesnt list d connectn in network manager when i connect my phone(usb) before powering on my laptop. though my phone is listed in d output to 'lsusb' in terminal. i hav to restart,wait until login screen appears and then connect d phone for d connection to be listed. anyway to fix this??

---

### Post by TechWiz2100 on 2011-02-27
try this from terminal while you are booted up with the phone not working```
sudo /etc/init.d/networking restart
```

---

### Post by vivek.pandey on 2011-02-27
> **TechWiz2100 said:**
> try this from terminal while you are booted up with the phone not working```
sudo /etc/init.d/networking restart
```

well i guess  this command has nothing to do with ubuntu recognising the device . it connects to net through wired network and also start networking is sufficient instead of sudo /etc/init.d/start networking. this works in backtrack

---

### Post by TechWiz2100 on 2011-02-27
> **neo_aryan said:**
> well i guess  this command has nothing to do with ubuntu recognising the device . it connects to net through wired network and also start networking is sufficient instead of sudo /etc/init.d/start networking. this works in backtrack

Learned something new today, didn't know init got its own command. However the OP said networking failed to auto detect a new network connection when the device was plugged in but is definitely recognized since the OP also said it appears when they ran lsusb.

The reason I said restart rather than start is because restart forces detection of devices and networking should already be started and running regardless of available connections so I assumed stopping networking would be in order. However you still have to do sudo start networking

---

