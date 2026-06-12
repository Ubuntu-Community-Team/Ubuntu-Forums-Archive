---
title: "help needed - can't enable wireless"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by altonis on 2010-01-07
Hello!

I have Ubuntu 9.10 installed on my laptop and TP-LINK TL-WN620G wireless device.

I think I have managed to install driver correctly, but I just cannot connect to my home wireless network. I can see the network name, when I open Network Connections panel, but Network manager says that "wireless is disabled". 

Could someone please give me a hint what to do?

---

### Post by nothingspecial on 2010-01-07
Don`t take this the wrong way but the first thing to check is that you`ve not turned the wireless off with a switch or a Fn button.

Also right click on the network icon in your panel and make sure Enable Wireless is checked.

If all is as it should be post the output of ```
sudo lshw -C network
```

---

### Post by altonis on 2010-01-10
Sorry for delay, I was not able to get online for a while.

However, I can't check in "enable wireless", it is not available.

---

### Post by nothingspecial on 2010-01-10
So, in your menus, go accessories > terminal

Then copy and paste
```

sudo lshw -C network
```

It will ask you for your password but you won`t see it when you type it.

Copy and paste the output into a new post in this thread.

No one can help you if they don`t know how Ubuntu is detecting your wireless card.

---

