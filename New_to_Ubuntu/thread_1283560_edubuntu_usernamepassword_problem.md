---
title: "edubuntu username/password problem"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by mjp29 on 2009-10-05
I installed edubuntu on my 4 years old laptop.

Now, when the laptop boots edubuntu asks for a username and then a password.  I set her Ubuntu up originally using the same username and password that I use on my other Ubuntu computer; however, edubuntu says that is the incorrect username or password.  Is there any way to determine the correct username and password?  Is there a way to fix this without having to do a complete reinstall from the CD?

---

### Post by BQAggie2006 on 2009-10-05
Try booting into single user mode, then check the /home directory or the /etc/passwd file to verify the account was created. If it was, then you can reset the password, if not you can create the account and set a password. Let us know if you need help with this procedure.

---

### Post by sisco311 on 2009-10-05
See this guide for step by step instructions:
[http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

---

### Post by mjp29 on 2009-10-05
> **BQAggie2006 said:**
> Try booting into single user mode, then check the /home directory or the /etc/passwd file to verify the account was created. If it was, then you can reset the password, if not you can create the account and set a password. Let us know if you need help with this procedure.

I tried what you I thought you said.  What I did was boot the computer with the live cd and clicked "place" then I clicked "home folder" but after that you lost me (in other words I had no idea how to check the /home directory or the /etc/passwd file (as I could not find or locate neither on the screen)

Nevermind about all of this, because the next post (below yours) linked me to a page where my wife actually figured it out [I was trying to do what was on the next post by booting the live cd and doing what was in the link but one has to actually remove the live cd and do it at that link without booting from a live cd].

Regardless of all this, I am now able to type in my chosen username and password and proceed.  However, I still have one question [below]:

- anyone know [or experienced] why edubuntu asks for a username and password upon booting when the user didn't have to offer that up when they installed ubuntu and chose not to ask for this?  After all here, I don't want my computer to bug me with this (although I know some people want it as they have house cleaners or other people around their computers that they don't want to allow them to boot up their computer and use it freely).  But I installed ubuntu the same way on this laptop (and selected to boot up without requiring a username/password) and when I chose to put edubuntu on my 4 year old daughters laptop it now asks for that.  She knows how to turn a computer on (she was using Ubuntu) and knew how to click to the firefox internet and find Dora the explorer.  However now after I put edubuntu on her computer she turns on the computer and she sees "ebuntu Username" and she just stares at it and eventually comes and tells me "daddy my computer is not working"

---

### Post by mjp29 on 2009-10-05
> **sisco311 said:**
> See this guide for step by step instructions:
[http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

I was unable to get this link to do what the link (not your fault) to do what the link told me to do.  However, at some point, my wife realized that we were still trying to boot from a live cd and should try what the link said to do without the live cd in the computer - and wholla (surprise) she then was able to figure this out and proceed to boot into edubuntu desktop and so forth.

I am marking this question as solved because of your very helpful reply and link.

However I would like to know one thing (maybe two or three things) which are:

1- why does edubuntu ask for a username and password when I installed Ubuntu on all my systems (2 systems) and I made a point to install Ubuntu in such a way that it would not ask for this when I turned my computer on and allowed it to boot up (I do not need this type of security at home).

2 - my wife told me that when she went through all the steps at your most helpful link that my username was my first name (which i tried to type in before with many attempts to type my name into that box with all lower case letters [like i knew it should be] and even first letter of my first name capitalized and the rest of letters lowercased.  I also typed in the same password that I use everywhere (including my 2 Ubuntu computers for adding/removing software or anything else which includes everything from buying things on amazon.com or bidding on ebay or logging on at work or answering to the ubuntu keyring (which i did away with because it bugged me way too much) yet I myself was unable to get past the edubuntu username and password boxes to get edubuntu to just boot up and work

3 - how do i make edubuntu not ask for a username and password and just boot up so my 4 year old (and my other daughter who is 6) can just turn on the computer and go about their business of using the computer (like they did when Ubuntu was on it).  Currently my 6 year old is smart enough where she is trying to type in a username [lord knows what she is typing in that box probably her first name] and then 6 year old daughter types something in the password box [i have no idea what she is typing in their either but i suspect she is is typing in my actual password as children at this/that age often hear things and since my password has never changed since the beginning of time [and she has heard me and her mother keep telling each other verbally "the password" she has learned it and is typing it in.  Which should make all parents not be surprised that their teens are accessing any on-demand or parent-prohibited channel on digital tv today as their kids usually know the password [even though we parents think they don't know the sacred password].  By the way, when my 4 year old sees the username/password screen come up she just comes and tells me she can't get her computer to work like it did before (believe it or not even the 4 year old was running/using Ubuntu by simply turning her little laptop Ubuntu computer on and finding Dora the explorer in the past before I decided to educate her and instal edubuntu.

4 - ok i didn't say i'd ask 4 questions, but how do i now tell edubuntu not to bug my 2 kids with user name/password because in the end game they come bug me to get past this step [a step that wasn't there before].

After I click "Submit Reply" below I will then mark this thread as Solved thanks to you - thanks!

---

### Post by sisco311 on 2009-10-06
[list=1]
[*]Load the Gnome Administration utility, 
click on System -> Administration -> Login Window 


[*]Change to the Security tab. 


[*]Enable the checkbox for Enable Automatic Login 


[*]Select the user account from the drop-down list of users.

[/list]

---

