---
title: "ubuntu"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by bigtoe on 2010-04-26
I updated ubuntu from 8.1 to 9.04 and for some reason it changed my password and I cant log in I would appreciate any help

                      thanks

---

### Post by sisco311 on 2010-04-26
> **bigtoe said:**
> I updated ubuntu from 8.1 to 9.04 and for some reason it changed my password and I cant log in I would appreciate any help

                      thanks

Odd... Try to boot into recovery mode and reset your password:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by wojox on 2010-04-26
You could try resetting your password: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Are you sure the CapsLock isn't on? I've never heard of an update changing your password.

---

### Post by wojox on 2010-04-26
> **sisco311 said:**
> Odd... Try to boot into recovery mode and reset your password:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

You're always ten seconds ahead of me. :P

---

### Post by sisco311 on 2010-04-26
> **wojox said:**
> You're always ten seconds ahead of me. :P

Just because I'm closer to the servers where the Ubuntu forums are hosted. ;)

---

### Post by bigtoe on 2010-04-26
still cant get anywhere

Screen says plug and play configuration error

also says running in low graphics mode

---

### Post by sisco311 on 2010-04-26
> **bigtoe said:**
> still cant get anywhere

Please post the error message you get when you try to log in.

---

### Post by bigtoe on 2010-04-26
pci number

---

### Post by cuberts on 2010-04-26
> **bigtoe said:**
> I updated ubuntu from 8.1 to 9.04 and for some reason it changed my password and I cant log in I would appreciate any help

                      thanksI thknk that you can recover the paragraph using the following steps:
Turn your computer on.

Press ESC at the grub prompt.

Press e for edit.

Highlight the line that begins kernel ………, press e

Go to the very end of the line, add rw init=/bin/bash

press enter, then press b to boot your system.

Your system will boot up to a passwordless root shell.

Type in passwd username

Set your password.

Type in reb

---

### Post by ttshivers on 2010-04-27
This Youtube video might help you.  It talks about reseting your password with the Ubuntu live CD.  [http://www.youtube.com/watch?v=AkENYv7kEhg&feature=player_embedded](http://www.youtube.com/watch?v=AkENYv7kEhg&feature=player_embedded)

---

