---
title: "Unable to copy the user's Xauthorization file."
date: 2011-07-12
forum: New to Ubuntu
---

### Post by n8cox on 2011-07-12
I have a new install of ubuntu and get the following error when trying to open Synaptic.

"Failed to run /usr/sbin/synaptic as user root. 
Unable to copy the user's Xauthorization file"

This is a brand new install.  I have not tweaked anything at all.  I tried reinstalling and it didn't change.  I have NO .Xauthorization file whatsoever.

Have read other posts and cannot find the issue or resolve it based on what I have read.  This is my very first attempt at creating a server.  Please Help.

---

### Post by n8cox on 2011-07-12
I guess a better question is what is the Xauthorization file?  How is it created?  And how can I get mine created?  I tried to run Xauth from the terminal but it was not successful.  Xauth is installed.

---

### Post by jerrrys on 2011-07-12
don't know how you got into such a mess, but open a terminal and enter

sudo chown chu:chu ~/.Xauthority

---

### Post by n8cox on 2011-07-12
K

Result was "chown: cannot access '/home/n8/.Xauthority': No such file or directory"

While installing it asks for me to name the server and when I type something other than what it recommends it says that the server name already exists.  I ignored that statement and continued anyway.  Would that have given me this issue?

---

### Post by n8cox on 2011-07-13
Please can anyone help?

---

### Post by skatinjj on 2011-07-13
Try this from the terminal:

```
gksu synaptic
```

or if you prefer

```
gksudo synaptic
```

Post back any error messages, if there are any in the terminal.

---

### Post by n8cox on 2011-07-13
A popup error came up saying:
"Failed to run /usr/sbin/synaptic as user root. Unable to copy the user's Xauthorization file"

And the terminal states,
"Error copying 'home/home/.Xauthority' to '/tmp/libgksu-Kg9Vrg': Permission denied"

The .Xauthority file does not exist so it will not be able to copy it.  I am assuming.  

Willing to try anything.  Please help.

Noticed that I do have an .Xauthority file in my home/username/ directory.  It has an X on the icon that I am assuming means that it is owned by root and I do not have access.  I guess that is progress because I didn't have that file before the last post.

---

### Post by n8cox on 2011-07-14
SOLVED!!!!!

Thank you all for your help.  I opened the terminal and typed:

gksudo synaptic

this apparently created the .Xauthority file

then I went back to the previous post and followed those instructions typing:

```
sudo chown username:username ~/.Xauthority     
```

(inserting my username in both instances of username above)
And the problem seems to be solved.
Thanks you again for your help!!!

---

### Post by skatinjj on 2011-07-14
> **n8cox said:**
> SOLVED!!!!!

Thank you all for your help.  I opened the terminal and typed:

gksudo synaptic

this apparently created the .Xauthority file

then I went back to the previous post and followed those instructions typing:

sudo chown username:username ~/.Xauthority     

(inserting my username in both instances of username above)
And the problem seems to be solved.
Thanks you again for your help!!!

That's great!

Please remember to mark the thread solved =)

---

### Post by zeugmatis on 2011-09-12
Solved for me - the file doesn't exist... so create it by opening a terminal and typing: 

touch .Xauthority

---

### Post by maddogmick on 2012-04-30
Thanks all followed this and it worked for me as well.
I tried the top remarks and it worked for one installation, but not the second, then I tried the last (touch) and that worked for the second.

Thanks again.

Mick

---

