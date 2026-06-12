---
title: "How do I run a script with a link?"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by matthewboh on 2007-03-19
I would like to be able to have a button to push to hook up to the VPN at work.  I've gotten it working, but I have to go into terminal mode and type several commands.  I'm running 6.10 ubuntu and would like to have an icon in the main system bar (the one with "Applications", "Places" "Systems" along with links to Evolution) that I can just click to have it connect to VPN, then I can click it again to disconnect.  Is that difficult?  How would I do it?  Would I be better off posting this in another area?  Thanks for all the help I've gotten in the past - these forums are great!Search

---

### Post by scxtt on 2007-03-19
turn whatever is involved in "I have to go into terminal mode and type several commands" into a script (post it here if you want some help) - then create a *button* that will invoke the script ...

---

### Post by matthewboh on 2007-03-20
Well, here's what I have to do to get VPN running...

```

sudo /etc/init.d/vpnclient_init start
password:
sudo vpnclient connect "High Speed Connection"

```

I also have to enter in a username and password at the connect, as well as answer yes to a prompt about keeping data private.

I would also love to have one that disconnects it too.

Thanks for the help!

---

### Post by scxtt on 2007-03-21
i don't know anything about "vpnclient" - is it a GUI program?  are you entering the username and password as well as the "yes" in the terminal or in a new GUI window the vpnclient opened?

what's involved in the disconnect?  more than just closing a window - or is "disconnect" considered running **sudo /etc/init.d/vpnclient_init stop**? ...

lastly, are you opposed to having **vpnclient_init** started @ boot?

---

### Post by matthewboh on 2007-03-21
> i don't know anything about "vpnclient" - is it a GUI program? are you entering the username and password as well as the "yes" in the terminal or in a new GUI window the vpnclient opened?


No, vpnclient is a terminal-based program.  I'm entering the username and password in the terminal (but the password is remembered).

> 
what's involved in the disconnect? more than just closing a window - or is "disconnect" considered running sudo /etc/init.d/vpnclient_init stop? ...


Right now, I have to leave the terminal window open where I ran the vpnclient connect command.  In order to disconnect, I have to open a new terminal window and type "sudo vpnclient disconnect".

> 
lastly, are you opposed to having vpnclient_init started @ boot?


I would love to have it start either at boot or right after login

Thanks again!

---

### Post by scxtt on 2007-03-21
you should be able to add a symbolic link to get "sudo /etc/init.d/vpnclient_init start" to happen @ boot ... put it in /etc/rc2.d/ as S99vpnclient ...

then make a script that runs your " sudo vpnclient connect "High Speed Connection" " and have a button that points to that script - most likely it should be able to be "run in terminal" ...

the script, named vpnclient_button_script.bash, would be of the form:

[indent]#!/bin/bash
sudo vpnclient connect "High Speed Connection"[/indent]

and the button would point to ~/vpnclient_button_script.bash

the same theory would work for disconnecting and be taken care of by another button, tho you could make the script be able to handle start/stop -- 1 step @ a time tho :p

---

