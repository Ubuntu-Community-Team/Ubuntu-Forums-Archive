---
title: "Need help in ssh"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by sandeep37 on 2009-03-04
I have two PC, but i use only my laptop. Now i want to uses those pc as backup . Is there any script using which i can start the PC without manually doing it,through SSH . I read it in LFY some time back. Can anyone help me with this. Thank you

---

### Post by ScruffyReid on 2009-03-04
I think this may be what you're looking for:

[http://ubuntuforums.org/showthread.php?t=234588]("http://ubuntuforums.org/showthread.php?t=234588")

It's not an SSH script, but it will allow you to wake your PC remotely.

---

### Post by Nepherte on 2009-03-04
It's not possible with SSH. A ssh server has to be running on the pc, which kinda rules out starting a computer over ssh.

---

### Post by mister_pink on 2009-03-04
Its possible that you could write a script that woke the computer with wake on lan, slept until it starts up, passwordly backs up with ssh then shuts it down with ssh. You should be able to google these things individually, wake on lan probably being the hardest to get working.

---

