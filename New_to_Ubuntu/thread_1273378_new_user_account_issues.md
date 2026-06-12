---
title: "new user account issues"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by toolmanpaul on 2009-09-23
Quote:
 	 	 		 			 				 					Originally Posted by **Omegaham** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7991835#post7991835") 				
 				[I]As long as you don't execute any attachments, nothing will get installed. Furthermore, with Linux you need to be root to install stuff. So, if a virus goes to install something, it will flash the "Install requires a password for administrative access" message.

Don't worry about it (unless you do all your stuff while logged in as root, in which case you should hit yourself and make your own user account).[/I]
 			 		 	 	 
[SIZE=4][COLOR=Red]tried to make new account..box pops up that says "not authurized to do this" but does not give me a log in to get to the root / ? what to do? [COLOR=DarkGreen]and[/COLOR] why should i hit myself??
[/COLOR][/SIZE]

---

### Post by scragar on 2009-09-23
You're confused between the user root who has access to everything on the system and the root file system. Don't worry, just do:
```
whoami
```If it says root then you've got a problem, if not then you're fine, you don't have write access(or shouldn't) to anywhere that can critically damage your system.

---

### Post by toolmanpaul on 2009-09-23
how do i log in as root? ... it never ask me anywhere that i can see

---

### Post by toolmanpaul on 2009-09-23
when i typed whoami  it listed my name ?  i already know that..?

---

### Post by A_Fiachra on 2009-09-23
> **toolmanpaul said:**
> how do i log in as root? ... it never ask me anywhere that i can see


sudo <command>


You don't want to log in as root, in general, but you do want to talk to your computer as a super-user, that's what the sudo command is for ... use it *sparingly*.

---

### Post by natravis on 2009-09-23
> **toolmanpaul said:**
> how do i log in as root? ... it never ask me anywhere that i can see

This is not advised. It is much better to log in normally, then use sudo to do whatever is necessary. If you really want to, at the splash screen where you can type in your username, you type root and the root password. If you don't ever see a login screen, you probably have it set to automatically log you in.

The whoami command saying your name is normal and what we wanted it to say. It means you are logged in as yourself and not as root. You do not want to be logged on as root normally.

---

### Post by toolmanpaul on 2009-09-23
i dont know commands...but i think i screwed something up cause now when i open "applications" there is no longer a "add and remove software" line there....how do i get add and remove back...i want to try digicam but cant add any programs anymore???

---

