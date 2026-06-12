---
title: "help getting apollon"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by jindosept on 2007-08-03
Hey, My friend runs apollon on his box and I really want to get it for my new ubuntu desktop.  I tried downloading it, but I get a message saying 

"Could not open the file /home/stimmer/Desktop/apollon-installer-0.8.1.run.  gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.  "

any idea how what to do for that?
thanks, big fan of this forum by the way

---

### Post by spd106 on 2007-08-03
Have you set the executable bit?

It can be done from a terminal by running this command
```
chmod +x ~/Desktop/apollon-installer-0.8.1.run
```

or you can do it via Nautilus, right-click select Properties, go to the permissions tab and ensure that the executable box is ticked. 

You may have to run it as root (sudo).

---

### Post by jindosept on 2007-08-08
When I hit > chmod +x ~/Desktop/apollon-installer-0.8.1.run the terminal says > chmod: cannot access `/home/stimmer/Desktop/apollon-installer-0.8.1.run': No such file or directory
When I type "apollon" in the terminal I get > X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found

I'm so screwed.   Do you know what I should do from here?

---

