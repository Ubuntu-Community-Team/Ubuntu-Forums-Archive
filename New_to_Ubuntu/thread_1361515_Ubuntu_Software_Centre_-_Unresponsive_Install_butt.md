---
title: "Ubuntu Software Centre - Unresponsive Install button"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by simpleblue on 2009-12-22
Ubuntu ver 9.1

I'm a newbie here, so please be gentle. ;)


I'd like to use the Software Centre to download programs. This is the message that displays in the terminal when I type "software-center":

> WARNING:root:_on_trans_error: org.freedesktop.PolicyKit.Error.NotAuthorized: ('system-bus-name', {'name': ':1.99'}) is not authorized: org.debian.apt.install-packagesIf anyone has ideas that would be much appreciated.

---

### Post by Elfy on 2009-12-22
and what happens when you use the menu button to run it?

---

### Post by simpleblue on 2009-12-22
> **forestpiskie said:**
> and what happens when you use the menu button to run it?
When I click on the Ubuntu symbol to the upper left hand side and select 'Ubuntu Software Centre' the response is the same, with the exception that the info does not show up in the terminal.

I'm not sure what you had meant by the question, but I hope this answered it.

Thank you for the suggestion.

---

### Post by Elfy on 2009-12-22
Yes that is what I was after knowing :)

Does Synaptic open? That is in the System Admin menu/

Does Add/Remove open - that _might_ be in the same menu.

---

### Post by simpleblue on 2009-12-22
> **forestpiskie said:**
> Does Synaptic open? That is in the System Admin menu/

Does Add/Remove open - that _might_ be in the same menu.
Synaptic does open... I checked out all the menus I could not find the Add/Remove program.

---

### Post by Elfy on 2009-12-22
OK - not really sure why software centre fails at the moment - I wasn't sure if you would have had add/remove - I think it is there but hidden - but it is going as sopftware centre is replacing it.

Try to purge and reinstall it 

```
sudo apt-get purge software-center &&sudo apt-get install software-center
```

---

### Post by simpleblue on 2009-12-22
> **forestpiskie said:**
> OK - not really sure why software centre fails at the moment - I wasn't sure if you would have had add/remove - I think it is there but hidden - but it is going as sopftware centre is replacing it.

Try to purge and reinstall it 

```
sudo apt-get purge software-center &&sudo apt-get install software-center
```
The purge/installation went well, but the result is the same thing. The button is unresponsive.


Thank you for your patience. I appreciate it.

---

### Post by prospero52 on 2010-01-14
I had the same problem..the install button would show that it was selected, but would do nothing. I am not a wizard at Linux by any means, but I found that the program was not invoking root.  I fixed my issue by going to System> Preferences> Main Menu and editing the Software Center Properties so that the Command' Box read 'gksu software-center'.  It then asked for root password on startup and the program ran fine.

---

