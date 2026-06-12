---
title: "ubuntu newbie - command line"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by Sparkatron on 2009-02-01
Hello there, I,ve installed ubuntu and slowly trying to get the hang of it.
My main use will be browsing and office apps. 
1        I would like some advice on security. The computer as it stands performs well under "grc shields up" but would i benefit from a firewall and if so whats the easiest way.
2        When i run the terminal program (command) and try a line that requires root access the line drops down and starts
  [sudo] password for user1:
  but I cannot enter anything, the cursor flashes after the colon but no keyboard entry, pressing enter just re-writes the line

Any help on these two would be appreciated

---

### Post by arochester on 2009-02-01
1) ufw.
2) Your password does not appear on the screen for security reasons. Just type it and press enter.

---

### Post by leonardo_neo on 2009-02-01
> **Sparkatron said:**
> Hello there, I,ve installed ubuntu and slowly trying to get the hang of it.
My main use will be browsing and office apps. 
1        I would like some advice on security. The computer as it stands performs well under "grc shields up" but would i benefit from a firewall and if so whats the easiest way.
2        When i run the terminal program (command) and try a line that requires root access the line drops down and starts
  [sudo] password for user1:
  but I cannot enter anything, the cursor flashes after the colon but no keyboard entry, pressing enter just re-writes the line

Any help on these two would be appreciated

1. You can use a firewall which is provided by the OS but not activated by default. To activate that use the following command

> sudo ufw enable

2. When you enter password in terminal, it doesn't 'show' what you are typing, so it appears as if nothing is happening. I recommend you to type your root password without worrying if it is showing or not, and then see if it was accepted or not?

---

### Post by Sparkatron on 2009-02-01
Thanks for help
Password working now, don't know what i was doing wrong before.

Firewall. I've dis-abled and re-enabled ufw in terminal, so I understand it to be running. Does this mean a degree of protection is already effective or do i have to configure settings.

---

### Post by Michael.Godawski on 2009-02-01
hi,

it depends what rules you want to add to the firewall:


[LIST]
[*][https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)
[*][https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)
[/LIST]

---

### Post by brian_p on 2009-02-01
> **Sparkatron said:**
> 

Firewall. I've dis-abled and re-enabled ufw in terminal, so I understand it to be running. Does this mean a degree of protection is already effective or do i have to configure settings.

For your intended use your Ubuntu install (+ updates) is guaranteed secure. Time spent in configuring a firewall (which will not make you any safer) would be better spent on learning and using the system.

---

