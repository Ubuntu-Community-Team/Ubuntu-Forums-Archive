---
title: "Send a string(password) to terminal"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by marius_vt on 2009-08-26
Hi Guys,
I have done this so far and getting my gnome-terminal to open and then start running another script.

I have only done this from command line. (Want to add all this to my startup at the end)

Here is what I have so far.
_Startup.sh_
#!/bin/bash
gnome-terminal --geometry=100x65 --title=Test --execute bash -c "sh Dynamips.sh ;bash"

_Dynamips.sh_
#!/bin/bash
sudo tunctl
sleep 1 
sudo ifconfig tap4 192.168.255.1 netmask 255.255.255.0 up
sudo /home/marius/./start.lab.sh
sleep 1
sudo /home/marius/Dynamips/IE/./start_lab.sh

It is working great when I run it from command line.

But

It asks me for my password due to sudo,
Is there a way I can send my password to the term within the script?
Keep in mind I want the script to run at startup.

Regards,

---

### Post by wojox on 2009-08-26
```
echo yourpassword | sudo -S command
```

---

### Post by marius_vt on 2009-08-26
Awesome,

Thank you very much,

The last script that runs launch a app called Dynamips

It is a terminal base program,

Will I be able to send some commands to the terminal(program) with echo?

If not how would I be able to do it.

Regards,

---

