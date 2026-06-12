---
title: "Update error"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by lolol i r linux noob on 2009-04-12
I get this error when trying to update

```
W: GPG error: http://ppa.launchpad.net intrepid Release: 
he following signatures couldn't be verified because 
the public key is not available: NO_PUBKEY 60D11217247D1CFF
```

can any one tell me how to fix this?

---

### Post by Paddy Landau on 2009-04-12
There are several ways to do this.

Here's one: See this thread:
[http://ubuntuforums.org/showthread.php?t=1047743](http://ubuntuforums.org/showthread.php?t=1047743)
Specifically, see post #5 for a nice script that you can use.

Here's another, quicker, way:
Enter this command in terminal
```
gpg --keyserver subkeys.pgp.net --recv 60D11217247D1CFF && gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
```Also see
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by lolol i r linux noob on 2009-04-12
this gets rid of the error message but updates arnt installed.

---

### Post by Paddy Landau on 2009-04-12
> **lolol i r linux noob said:**
> this gets rid of the error message but updates arnt installed.

[LIST=1]
[*] Open Update Manager (Administration -> Update Manager).
[*] Press the button labelled "Check".
[*]If it's available, press the button labelled "Install Updates."
[/LIST]
 If it still doesn't update, then let us know which package specifically is giving you the problem, what version you already have, and what version of Ubuntu you're using.

---

### Post by lolol i r linux noob on 2009-04-12
its worked now
guess there was something wrong with me connection or summut

---

### Post by Paddy Landau on 2009-04-12
> **lolol i r linux noob said:**
> its worked now
guess there was something wrong with me connection or summut
Sometimes these things happen!

Thanks for letting us know.

---

