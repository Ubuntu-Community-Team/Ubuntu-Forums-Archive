---
title: "I have big problems!"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by jakethesnake123 on 2011-04-05
Hello

I have managed to mess it up pretty decent for me so I need your help.

It started when I installed OpenVPN because I wanted to use me by an anonymous VPN service, but I ran into problems with the configuration so I tried to install NetworkManager-gnome and I did not work either.
Now Wicd-NetworkManager disappeared from the K-menu for some reason and I manage to not start it from the console and it's the same with NetworkManager-gnome. Where did my Wicd way from the K menu? Can not find my internet and connect to the internet even after that I do not know what the command is in the console for this. Now asking you for help to get my Wicd-NetworkManager back in K-menu and also remove NetworkManager-gnome.

Thanks in advance!

---

### Post by arochester on 2011-04-05
Generally you can only have one networkmanager at a time. If you install one it removes the other.

If you can, connect your computer temporarily by cable. Then, connected to the Internet, open a Terminal and input: sudo apt-get install wicd.Reboot

That should sort you out.

---

### Post by jakethesnake123 on 2011-04-05
> **arochester said:**
> Generally you can only have one networkmanager at a time. If you install one it removes the other.

If you can, connect your computer temporarily by cable. Then, connected to the Internet, open a Terminal and input: sudo apt-get install wicd.Reboot

That should sort you out.

I understand that by now. Yes i can connect my laptop to the cable, but then comes the problem that i don't know how to connect to it. I don't have any auto-connect configuration. Before i always connected my cable or wifi via the graphic wicd-manager. So how do i do to find my cable and connect to it via the console?

---

### Post by JamesBartlett on 2011-04-05
I do apologise as this comment won't directly help you. You should include some info about your problem in your title, as then someone will scan through the titles, and think: 'Ah, I've dealt with that problem successfully befor, I'll help this guy/girl'. Your problem should get solved far quicker. Be wary of posting the same problem twice, the moderators don't take kindly to that. The best of luck with your problems, and apologies I acan't help.

James

---

### Post by rosencrantz on 2011-04-05
Ubuntu command line networking howto:
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

---

