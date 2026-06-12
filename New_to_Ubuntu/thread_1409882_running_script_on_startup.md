---
title: "running script on startup"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by dineshs on 2010-02-18
I run a script each time I start my machine for sharing internet.How can I do this automatically? I followed this link 
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)
,but when I run the command```
sudo update-rc.d myscript start 51 S .
```
it says 
update-rc.d: warning: /etc/init.d/dinesh missing LSB information
How can I solve this?

---

### Post by lijcam on 2010-02-18
An quicker way to do this is with crontab.

Open the terminal
```
crontab -e
```and add this
```
@reboot /path/to/your/script/your_script.sh
```Make sure your script is executable.

---

