---
title: "Newly installed ubuntu error and no log-in"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by University on 2010-03-09
Hi
 
I yesterday installed Ubuntu 9.10. having only very little experience with it. It worked fine and I was amazed with it, but today there is a problem coming up.
 
When I start the computer, it gives me a warning window that sais: "**Could not update ICEauthority file/home/user/.ICEauthority**."
 
After clicking OK, a second one comes up "**There is a problem with the configuration server. (/usr/lib/libgconf2-4geonf-sanity-check-2 exited with status 256)"**
 
A third message sais "**Nautilus could not create the following required folders: /home/user/Desktop,/home/user/.nautilus. Before running Nautilus, please create these folders, or set permissions such that the Nautilus can create them."**
 
Then another message comes up saying "**Record your encryption passphrase**.....etc"(I did not write this one down).
 
Then computer hangs at an empty Ubuntu brown screen seemingly doing nothing.
In other words, I can't log in.
 
Of course, I have no idea what all these messages mean.
 
The last thing I remember doing before this happened was enabling the integrated firewall and trying to stop the sounds that play at Ubuntu startup.
 
Please help me.

---

### Post by r-senior on 2010-03-09
It sounds like your user ID doesn't have access to its own directory for some reason?

If you press Ctrl-Alt-F1, do you get a login prompt where you can login successfully?

If so, try:

$ ls -lA

and see who owns the files. They should all be owned by "user", if that's your user id. It's the third column in the listing.

---

### Post by University on 2010-03-09
that's right, mu user name is "user"
 
so I pressed Control+Alt+F1 and I was asked for my username, then my password
 
I gave it the correct ones, now it sais:
 
[EMAIL="user@user-laptop:~$"]user@user-laptop:~$[/EMAIL]
 
is this where I put the "ls -lA" ?
 
and is that "l" a small-case "L" ?

---

### Post by University on 2010-03-09
so I pressed "ls -lA" and it gave me a bunch of data.
 
it is a list of information, it sais for example:
 
drwxr-xr-x 2 user user 4096 2010-03-09 01-02 [COLOR=blue]Desktop[/COLOR]
[COLOR=#0000ff][/COLOR] 
[COLOR=black]and it goes on with similar info for Documents, Downloads, etc.[/COLOR]
 
 
What does this mean? and how do I fix my problem?

---

### Post by University on 2010-03-09
So now I'm left at that page with all the data, and it sais [EMAIL="user@user-laptop:~$"]user@user-laptop:~$[/EMAIL] and apparently waits for a command.
 
I don't know much about Ubuntu. I don't know what to try, even any simple thing.
 
I want to make everything OK as it was before this problem. Where I can switch on my computer and log-in normally.
 
 Please let me know of any idea, even if it's a simple one.

---

### Post by University on 2010-03-09
Hi.
 
I am in my university, and I will have to go home in a while. So I won't have a computer to check back here.
 
Noone gives me an answer to my problem. Does this mean I somehow screwed up seriously and that my problem is rare or without solution?
 
I also want to ask if this kind of problems are common for Ubuntu. Did it happen becuase  I did something wrong (I only did what I explained above before this happened) , or do these problems can happen even "out of nowhere"?
 
I am not looking forward to returning to my previous OS after seeing how great Ubuntu is (at least at first glance).
 
What should I do now? Is my only choice a clean re-install of OS ? Please someone try to help me out

---

### Post by halitech on 2010-03-09
look for the entry .ICEauthority and see what the permissions are for it. According to mine, it should look like this
> -rw-------   1 daryl daryl   34297 2010-03-09 08:25 .ICEauthority

as far as not getting an answer, everyone here is volunteers so the people who are around may not have an answer, sometimes it takes some time for the right person to see the question and give you a response.

---

### Post by University on 2010-03-09
halitech, thanks for your responce.
 
I am really unlucky today! :) My computer's battery is now empty. 
 
I will have to go home. I will try to borrow a housemate's computer to communicate here and I'll try what you said.

---

### Post by r-senior on 2010-03-09
> **University said:**
> So now I'm left at that page with all the data, and it sais [EMAIL="user@user-laptop:~$"]user@user-laptop:~$[/EMAIL] and apparently waits for a command.
 
I don't know much about Ubuntu. I don't know what to try, even any simple thing.
I do apologise. :oops:

I should have added that to get back to your X-Windows environment, press Ctrl-Alt-F7.

If the listing produced by "ls-lA" looks OK (the third column is the owner of the file), and it does by the sound of it, it's not the problem that I thought it might be. halitech's suggestion would be next to try, but doesn't explain why things like Desktop are not being recognised by Nautilus.

---

### Post by oingk on 2010-03-09
hi
I am "Universiy" (I didn't want to log in with this account from my uni, because I think that my university is plotting against me).

no worries r-senior, I should have emphasised more how clueless I am.

Now I came home and I'm using a Ubuntu LiveCD that fortunately I have.

OK. So how do I do what halitech suggests?how do i look for entry .ICEauthority?

---

### Post by oingk on 2010-03-09
oh, maybe I should add the information that upon installing my Ubuntu, when I was asked if I want to password-protect my log-in and/or my home directory (or something like that) I chose "yes" to both.

Don't know, maybe this makes a difference for you to understand.

---

### Post by asharpham on 2010-03-11
I'm pretty new to Ubuntu as well but to get to a file with a . in front of the filename you need to be able to view hidden files. Click on View then check Show Hidden Files. Someone else may know where .ICEauthority is but if you click Places-->Computer-->filesystem (double click filesystem), then Search on .ICEauthority (be careful with upper case as Ubuntu is case sensitive unlike Windows).

I hope this helps a bit. As I said, I'm pretty new to Ubuntu myself but I've learnt a little over the last couple of months.

Alan.

---

### Post by josh.wright on 2010-03-15
Hello,

I've got a similar problem on a laptop running 9.10. I checked the .ICEauthority file if the user ID was correct, which it is, same goes for the home directory and .nautilus.

The last thing I did before everything went wrong was changing a password. This can't have caused the problems could it?

---

### Post by josh.wright on 2010-03-31
Searched through all the files, checked permissions and couldn't find any problems :cry:, I must have somehow upset the operating system when I stormed about changing passwords so I've gone & reinstalled it, though there could be a way around it and I wasn't patient enough to find a way.

---

