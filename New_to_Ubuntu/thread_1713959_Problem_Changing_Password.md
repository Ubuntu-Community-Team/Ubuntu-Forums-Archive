---
title: "Problem Changing Password"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by patch953 on 2011-03-24
I set a simple 2 letter pasword when I installed Ubuntu 10.04. I am now trying to change it to something that is still short and simple. I read in another thread to edit /etc/pam.d/common-password. 

The line now reads:
password         [success=1 default=ignore]         pam_unix.so min=2 sha512

I've rebooted but I'm still getting the dialoge about the new password being too short or if I try a longer one it's too simple. I thought that deleting "obscure" eliminated this.

---

### Post by patch953 on 2011-03-25
I really need n answer to this. Will someone please give it a try.

---

### Post by Frogs Hair on 2011-03-25
I'm not sure what exactly you have done , but try this. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by crispy_420 on 2011-03-25
This may sound weird but if read my reference right try this:
Leave "obscure" in. Also add max=2 after the min=2. Sounds odd right? The max just stops looking at complexity on passwords over said number. So you should have:

password [success=1 default=ignore] pam_unix.so obscure min=2 max=2 sha512

Reference: [https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)

Scroll down to password section about half way through.

---

### Post by patch953 on 2011-03-25
That worked. Thank you.

Is there no way to get rid of the "obscure" requirement using the GUI? I had seen that article before, but did not want to mess around at that level. I hope they change this in another release. I don't think we need an OS second guessing the human without a simple way to over ride it. If passwords can be reset this easily then what is the point of requiring them, much less complicated ones?

---

