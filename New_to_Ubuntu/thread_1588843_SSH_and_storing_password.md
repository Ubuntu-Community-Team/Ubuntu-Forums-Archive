---
title: "SSH and storing password"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by Mauler5858 on 2010-10-05
Alright, here is my situation.  I administer a UNIX box that runs Teamcenter Engineering software.  I need to create a slew of scripts that need some of the functionality from Linux that UNIX doesnt offer( i.e. performing arithmetic on the date command).  I have a little Ubuntu Server box that runs a MediaWiki for my group, that I would like to use just to run some commands against. I have already got what I needed in order to actually run the command from UNIX over ssh to the box and return the result.  I just need it to do this password-less so i can automate this into a script.  How can I do this without compromising the security of either box?

---

### Post by HermanAB on 2010-10-05
Howdy,

Use ssh-keygen and copy the public key to the distant box /.ssh/authorized-keys file.

---

### Post by cariboo on 2010-10-05
Just to add to what HermanAB said, have a look at [this]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") document.

---

