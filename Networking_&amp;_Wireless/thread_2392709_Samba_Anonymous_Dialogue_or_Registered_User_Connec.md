---
title: "Samba Anonymous Dialogue or Registered User Connect button"
date: 2018-05-24
forum: Networking &amp; Wireless
---

### Post by Axis Mann on 2018-05-24
Security = Share is no longer a valid security model!  For some time now when I connect to a guest only share in nautilus network places for  another computer in my LAN, I have to suffer seeing a modal dialog box that ask me if I  want to connect anonymously or as a registered user.  I setup the guest share using the options security=user, guest ok = yes, guest only =yes, guest account = myuser, map to guest = bad user, yada, yada, yada, so I could allow any user to connect to this guest share anonymously, without a password. 

 I use to code security=share in the smb.conf file so I wouldn't be prompted after clicking on the guest share I wanted to open.  But now, with security=user, the user has to also click a connect button on a modal dialogue that pops up after clicking the guest share to be opened.

  Is there something I can change to prevent seeing the modal dialogue with connect button when connecting  anonymously to a guest ok share.  I don't have to supply a password to connect anonymously so why do I have to suffer through yet another click for an additional dialogue box that ask me if I want to supply a password or connect anonymously after I already clicked on the share that is set up to connect without a password?  I want to connect to anonymously.  I'm not looking for advice on security.  I'm just trying to restore the behaviour I had on my samba network for my linux computers before the security=share option was finally pulled after years of deprecation.

---

### Post by Axis Mann on 2018-05-25
All I've come up with so far as a work around is to select the connect as registered user radio button on the Anonymous or Registerered User modal dialogue prompt, and supply the user's password and click the remember forever radio button at the bottom of the dialogue panel.  I then no longer get asked if I want to connect anonymously or as a registered user in subsequent attempts to access the guest-only share but an entry gets made in my gnome keyring when I do that. 

 But, since I'm using autologon when I boot my computers, the keyring doesn't get opened until I access some service that needs a password from the keyring such as connecting to my guest-only share as a registered user.  Therefore, using this connect as registered user workaround results in the display of a dialogue panel that requests that I unlock the keyring.  So, I've only succeeded in replacing the Connect as Anonymous or Registered User prompt with one to unlock the keyring.  That's no less annoying than the original problem that popped up with the removal of the security=share option from samba.  It's an anonymous share with guest access!  I simply don't have a need to use a password to access this share.

Can anyone offer a different solution to this problem when using security=user?  I don't like my workaround because I still get a prompt to enter password to unlock my login keyring instead of the connect as anonymous or registered user prompt I get without using my workaround to avoid that prompt.  Any suggestions? Has anyone else experienced the same or similar inconvenience?

---

### Post by Axis Mann on 2018-05-25
For the time being, I continue to use auto log-on and click on the connect button when the Anonymous or Registered user dialog box is displayed after I click on a guest share in nautilus network places that I want to access.  I didn't like my previous workaround to log in as a registered user because it requires that I log-on manually with password when I boot my workstation or suffer through a prompt to unlock my keyring when I try to access a guest share.  I could delete my keyring password but then, according to comments I've seen, that will leave my stored passwords unencrypted.  I haven't decided yet if that is a bad thing for me since I already log on without a password and avoid remembering passwords for all the sites I connect to.

---

