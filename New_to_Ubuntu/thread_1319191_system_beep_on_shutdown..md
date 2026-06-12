---
title: "system beep on shutdown."
date: 2009-11-08
forum: New to Ubuntu
---

### Post by ja660k on 2009-11-08
hey all,
I recently installed 9.04, and im happy with it but when i go to shutdown the system from gnome menu.. the system beeps 3 times in succession then shutsdown normally.

how can i stop this.

ps; xset -b 
doesnt work in the case

thanks :-)

---

### Post by Zoot7 on 2009-11-08
Running
```
sudo modprobe -r pcspkr
```

should disable it until you reboot.

To disable it permanently, run this:
```
echo 'blacklist pcspkr' | sudo tee -a /etc/modprobe.d/blacklist
```

You should be beep free then.

---

