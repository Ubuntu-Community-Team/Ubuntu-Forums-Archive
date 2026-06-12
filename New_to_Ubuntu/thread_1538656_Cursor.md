---
title: "Cursor"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by rclesueur on 2010-07-25
My cursor is a plain white box, about a centimeter on a side.  It works and I can use it but it is a pain to get it positioned correctly and since it is white, dissappears on a white background and covers text and graphics when in other backgrounds.  I have Ubuntu 10.04, my computer with a K8M890 chip set and a Samsung LCD display.  I have downloaded OpenChrome and installed it.  Here is a command I entered that might be helpful:

roger@LeSueur:~$ sudo lshw -C display
[sudo] password for roger: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: K8M890CE/K8N890CE [Chrome 9]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 11
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: latency=64 mingnt=2
       resources: memory:d0000000-dfffffff(prefetchable) memory:fa000000-faffffff memory:fbcf0000-fbcfffff(prefetchable)
roger@LeSueur:~$ 

How do I fix this!!!!!!!!!!  Please!!!!!!!!!!!!!!

---

### Post by collinp on 2010-07-25
A "blank white box" sounds like you're missing the cursor itself...

System -> Preferences -> Appearance Preferences, click "Customize" while having your current theme highlighted, then click "Pointer" and try some of the different settings there to see if it makes any difference.

---

### Post by rclesueur on 2010-07-25
I've tried all the themes, changing cursors, and everything I could find in Ubuntu.  Thanks for the suggestion.  Are there anymore suggestions???

Thanks for the time.

---

### Post by collinp on 2010-07-25
That certainly odd...

It might be a configuration issue. Try the following command:
```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

That will reconfigure the Xserver (what allows you to display graphics), then restart the Xorg (it'll take your current GUI session with it).

---

### Post by rclesueur on 2010-07-25
I did that and still have a white box instead of a cursor.  Thanks for your idea.  Any other ideas?

---

### Post by paultag on 2010-07-25
Have you tried turning off desktop effects? It could be a compositing issue

---

### Post by rclesueur on 2010-07-25
Desktop effects are off.  Same issue.  Thanks for the suggestion.

---

