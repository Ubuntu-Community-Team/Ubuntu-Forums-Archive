---
title: "empathy help"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by namluc on 2010-04-04
i need help with empathy.

i want to encrypt my past conversations, find the button that easily deletes them, and also find the option to never record them. 

thanks everyone, wishing everyone a happy special sunday

---

### Post by NightwishFan on 2010-04-04
I am not sure if Empathy has those features. Perhaps try the Pidgin instant messenger. It is included in the Ubuntu repositories, just search for 'pidgin'. You can wait for other responses first though if you want. I never need anything more than a box to chat in myself.
[http://en.wikipedia.org/wiki/Pidgin_%28software%29](http://en.wikipedia.org/wiki/Pidgin_%28software%29)

---

### Post by @rizz on 2010-04-04
Hi there,

  Great question!!!

 But i don't think it does. we can view our previous conversations but i couldn't even clear that...???

 Here's a link on the same problem that has been well discussed in the past:

  [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/296867](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/296867)

---

### Post by namluc on 2010-04-04
Hmm. i thought i was just being really stupid? So let me get this right.

empathy can and does record conversations of everyone. 
those conversations are available at the click of a button, they are not password encrypted, anyone can view them. 
there is no easy option to delete them
and it is not possible to turn off the record conversations feature

hmmm

---

### Post by NightwishFan on 2010-04-04
Check if they are able to be deleted by going to View -> Previous Conversations.

hmmm....

---

### Post by namluc on 2010-04-04
nope even right click and clear doesn't work, as the convo pops back when reselected.

imagine this situation
i talk to person A about person B
i go to the toilet
person B reads my convesations
i return to a very angry person B

maybe i could lock the screen, but that just looks paranoid

who could i sue to compensate me for lost whatever owing to the anger of person B?

i could use pidgin, but empathy does LOOK a bit more polished even if it actually is a piece of crap, as i am finding out now.

ok

what would be the terminal command to delete all of my empathy conversations

---

### Post by NightwishFan on 2010-04-04
I am unsure. Unless what you are saying is hypothetical, I would advise anything that may make B angry is better left unsaid by A. However A being a reasoning logical being, he/she can make his/her own mind. ;)

I really wish I could help you. I am not a fan of Empathy either (apart from it's interface and desktop integration). It is a platform to grow from, it is not quite there yet.

As for deleting the logs. They are in hidden files in your home folder. Open the Home Folder and press ctrl+H to show hidden files, then look here. I have heard rumour they are in any of these places depending on the version of empathy. :lolflag:
~/.gnome2/Empathy/logs
or
~/.local/share/Empathy/logs
or
~/.local/share/empathy

For now I advise locking your screen. Here is a link.
[https://bugs.launchpad.net/empathy/+bug/411898](https://bugs.launchpad.net/empathy/+bug/411898)

---

### Post by @rizz on 2010-04-04
go to 
 ```
cd ~/.local/share/Empathy/logs/
```there type ```
$ ls
```it will show you a Directory that starts with the name gabble_jabber......so on

go inside that and u will find all the conversation in tiny folder named after the people u chatted with........

delete them if you want......

that should do the job

your security is your responsibility:mrgreen:

---

### Post by namluc on 2010-04-04
ok thanks everyone, all deleted now. I must say though, its a bit ridiculous not having control over my information.

is there a terminal command where i can turn off conversation logging?

---

### Post by da burger on 2010-04-04
If you want a launcher to delete them all at once the command is ```
rm -r ~/.local/share/Empathy/logs
```

---

