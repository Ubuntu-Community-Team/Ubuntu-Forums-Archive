---
title: "send notification from pc to andoid"
date: 2019-12-14
forum: Networking &amp; Wireless
---

### Post by jduns on 2019-12-14
To send a notification from pc to andoid once I useed [notify.sh]("https://github.com/mashlol/notify"), but now it's an app impossible to get (for andoid).
What is your advice? Using KDE-connect? But how?
Thank you!

---

### Post by jduns on 2019-12-14
I should use kdeconnect-cli, I know: but when I try with 
    [FONT=fixedsys]kdeconnect-cli --ping-msg "hello!"[/FONT]
I get this error message:
    [FONT=fixedsys]No device specified[/FONT]

---

### Post by SeijiSensei on 2019-12-14
kdeconnect-cli has a lot of options. See "kdeconnect-cli --help" for a list. My guess is you need to specify a "device ID" or a "device name." Running "kdeconnect-cli -l" returns a list of visible devices. My phone appears as
```
lge: d9a8cf5491c9b5f2 (reachable)
```

Once I paired the devices using the GUI app on my PC, I could ring my phone with "kdeconnect-cli -d d9a8cf5491c9b5f2 --ring".

---

### Post by jduns on 2019-12-14
Thank you. Yes, I know: but where should I put the device name/ID? Whatever I try I get always an error message: Device not specified...
No, I'm wrong: I have to add -d, or -n.
So no error message. 
But also no message on smartphone...

EDIT
this [B]works

[/B]kdeconnect-cli --ping-msg "hello!" -d d30fdc9ed6e2bf56Thanks!

---

