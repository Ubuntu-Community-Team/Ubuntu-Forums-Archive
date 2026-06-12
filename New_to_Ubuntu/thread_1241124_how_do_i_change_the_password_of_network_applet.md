---
title: "how do i change the password of network applet?"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by steve19137 on 2009-08-15
self explanatory. i dont want to type a password in every time i reboot, so i also want it to remember the password.

---

### Post by RedSingularity on 2009-08-15
System>Admin>Login window.  Go to the security tab.

---

### Post by mcduck on 2009-08-15
> **steve19137 said:**
> self explanatory. i dont want to type a password in every time i reboot, so i also want it to remember the password.

Are you using automatic login?

To remove the prompt for keyring password when using automatic login you'll have to remove the keyring password completely. Go to Applications/Accessories/Passwords and Encryption keys, then on the Passwords-tab right-click the login keyring and select "Change password". Type your old password but leave fields for new one empty. You'll get a warning asking if you really want to store your passwords unencrypted, but since you are already using automatic login that probably isn't an issue for you..

---

### Post by steve19137 on 2009-08-16
> **mcduck said:**
> Are you using automatic login?

To remove the prompt for keyring password when using automatic login you'll have to remove the keyring password completely. Go to Applications/Accessories/Passwords and Encryption keys, then on the Passwords-tab right-click the login keyring and select "Change password". Type your old password but leave fields for new one empty. You'll get a warning asking if you really want to store your passwords unencrypted, but since you are already using automatic login that probably isn't an issue for you..

thanks it worked. will i have to enter a password anymore if i want to install something new, or if i use the "sudo" command?

---

### Post by earthpigg on 2009-08-16
yes, sudo will still ask for a password.

google search 'enabling root account ubuntu' if you never want to enter your password - be warned, however, that you will be intentionally bypassing/disabling most of the things that make linux more secure than Windows by logging in as root on a regular basis for every-day computing. the vast majority of linux users will tell you that it is incredibly foolish but, hey, it is your computer.

it is so foolish, in fact, that it is against ubuntuforums.org policy for us to explain to you how to do this here.

---

### Post by steve19137 on 2009-08-16
> **earthpigg said:**
> yes, sudo will still ask for a password.

google search 'enabling root account ubuntu' if you never want to enter your password - be warned, however, that you will be intentionally bypassing/disabling most of the things that make linux more secure than Windows by logging in as root on a regular basis for every-day computing. the vast majority of linux users will tell you that it is incredibly foolish but, hey, it is your computer.

it is so foolish, in fact, that it is against ubuntuforums.org policy for us to explain to you how to do this here.

lol, against policy. but no, i dont want to turn off sudo password. i just wanted to make network applet not pop with a password every reboot. thanks for the help

---

### Post by colau on 2009-08-17
> **Shadow121 said:**
> System>Admin>Login window.  Go to the security tab.
Thank you.

---

### Post by colau on 2009-08-17
> **Shadow121 said:**
> System>Admin>Login window.  Go to the security tab.
Is there any security problem for automatic login?

---

### Post by earthpigg on 2009-08-17
> **steve19137 said:**
> lol, against policy.

not joking dude, it is.

---

### Post by earthpigg on 2009-08-17
> **colau said:**
> Is there any security problem for automatic login?

assuming you maintain physical control of your computer, no there is not.

---

