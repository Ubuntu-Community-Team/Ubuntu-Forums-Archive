---
title: "Networking credentials"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by Bronto on 2007-04-18
Please, I really need someone smarter than me to put me on the right track here.

First some relevant background:

I have a file server running the SME Server distribution (CentOS based).

I've created a folder on this server where every user can add, edit, delete files and folders.
Let's call this folder "common_files".

Now, let's say I'm adding a new user called user_one to this server and I set it's password to "secret_pass". A lot of things happen automatically but only two are relevant to this post.

1. The server automatically grants user_one the rights to access the "common_files" folder.

2. The server automatically creates the "user_one" folder which only user_one can see over the network.

Now, to the subject:
If I login into a Windows box (98, XP, whatever) as "user_one" using "secret_pass" as password, I can access and use from Network Neigborhood the "common_files" and "user_one" folders.

If I login into a Ubuntu box as "user_one" using "secret_pass" as password, the circus begins.

First, I cannot see the "user_one" folder in Places/Network/Windows Network(!?!?)/Sever.
 
Second, I have to enter the username and password to access the "common_files" folder and I have the option to save this password into a passworded keyring for future use (O, happy day!!!).

And finally, the questions:
1. Windows to Linux networking works better than Linux to Linux networking?
2. Why do I have to access a "Windows Network" into a pure Linux environment?
3. Why a Ubuntu box is by default a member of the MSHOME workgroup?
4. How can I instruct my Ubuntu box to use the login credentials for networking?

Thank you for your time,
Bronto

P.S. I am perfectly aware that i can solve the problem by using fusesmb.

---

### Post by Bronto on 2007-04-18
Well, I am pleased to say that Kubuntu solved the (connection to shares) problem.
It has an option in kcontrol called "Local Network Browsing".
Here you can enter a default username and password to access network shares.

I'm still curious about the MSHOME default workgoup...

---

### Post by johnbick on 2007-04-23
Where do we find KControl? looked all over for it -- except in the place it "hides out"! 
(I'm a newbie, obviously...)

---

