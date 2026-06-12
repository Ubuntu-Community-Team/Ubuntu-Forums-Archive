---
title: "Full Path of mail client"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by daniell59 on 2010-05-16
My link in firefox no longer works. I have been trying without success to fix it. This is a learning process for me. First off I have to find the full path of the mail client. I would appreciate it if someone could explain to me how to achieve this. It would also be nice if someone could guide me the rest of the way.

Thanks in advance

---

### Post by oldos2er on 2010-05-16
If you're using evolution, the path is /usr/bin/evolution

---

### Post by jd65pl on 2010-05-16
```
which {program name}
```

```
user@host:~$ which kmail
/usr/bin/kmail
```

---

### Post by daniell59 on 2010-05-16
> **oldos2er said:**
> If you're using evolution, the path is /usr/bin/evolution

I should have said Thunderbird

---

### Post by ajgreeny on 2010-05-16
Also make sure that Thunderbird is set as the default mail program in **System ->Preferences ->Preferred Applications**, where it will be evolution at the moment, if you have not already changed it.

---

### Post by daniell59 on 2010-05-16
I typed in /usr/bin/thunderbird but the link still does not work.

---

### Post by daniell59 on 2010-05-16
I think that my path is different. Can someone please explain to me how I determine what my path is. My knowledge is limited, but I am trying to learn.

Thanks

---

### Post by ajgreeny on 2010-05-16
As jd65pi said ```
which thunderbird
``` will give you the full path.

---

### Post by Excedio on 2010-05-16
```
thunderbird %u
```

---

### Post by daniell59 on 2010-05-16
> **ajgreeny said:**
> As jd65pi said ```
which thunderbird
``` will give you the full path.

Thanks, I had the correct path, but it still would not work.

Any ideas?

---

### Post by Excedio on 2010-05-16
> **daniell59 said:**
> Thanks, I had the correct path, but it still would not work.
 
Any ideas?
 
Open a terminal and type in
 
```
thunderbird %u
```
 
if that does nothing or you get an error
 
```
thunderbird
```

---

### Post by daniell59 on 2010-05-16
> **Excedio said:**
> Open a terminal and type in
 
```
thunderbird %u
```
 
if that does nothing or you get an error
 
```
thunderbird
```

What I meant was that I still cannot get firefox to provide a mail link.

---

### Post by Excedio on 2010-05-16
> **daniell59 said:**
> What I meant was that I still cannot get firefox to provide a mail link.
 
I'm thinking that I just don't understand what you're trying to do. I've read the thread multiple times, but I'm just not understand what it is that you want.

---

### Post by daniell59 on 2010-05-16
> **Excedio said:**
> I'm thinking that I just don't understand what you're trying to do. I've read the thread multiple times, but I'm just not understand what it is that you want.

I am sorry for the lack of clarity.
Ok, When I am in Namoroka, I want to send a link of the page to a friend with the email. I hope that this makes things more clear.

---

### Post by Excedio on 2010-05-16
> **daniell59 said:**
> I am sorry for the lack of clarity.
Ok, When I am in Namoroka, I want to send a link of the page to a friend with the email. I hope that this makes things more clear.
 
Nope, sorry, still not understanding what you are attempting. Can you provide steps as to how you *used to* do this?
 
...I really hope I'm not the only one not understanding this...

---

### Post by daniell59 on 2010-05-16
> **Excedio said:**
> Nope, sorry, still not understanding what you are attempting. Can you provide steps as to how you *used to* do this?
 
...I really hope I'm not the only one not understanding this...

While in Firefox I would do the following.

File
send link
Thunderbird would come up with the link included. I would put in the email address, then press send.
I hope that I made things clearer. It stopped working today.

---

### Post by EssexEagle on 2010-05-16
> **daniell59 said:**
> While in Firefox I would do the following.

File
send link
Thunderbird would come up with the link included. I would put in the email address, then press send.
I hope that I made things clearer. It stopped working today.

Where are you trying to enter the path to the mail client?

---

### Post by Excedio on 2010-05-16
> **daniell59 said:**
> While in Firefox I would do the following.
 
File
send link
Thunderbird would come up with the link included. I would put in the email address, then press send.
I hope that I made things clearer. It stopped working today.
 
Yes. Now it's clear to me. :-)
 
However, I never use that and have no clue how to fix it :-/

---

### Post by cuberts on 2010-05-16
> **oldos2er said:**
> If you're using evolution, the path is /usr/bin/evolutionit really depends on the mail client. Please give more information.

---

### Post by mgmiller on 2010-05-16
In Firefox, (namoroka) click on Edit > Preferences and go to the Applications tab.  Scroll down till you see "mailto" on the left side.  On the right side will be the mail program it's associated with.  The default is evolution.  Click the down arrow to the right and you should get a list of the mail programs, just select thunderbird, or if it's not listed, try "Use Other" and browse to it.  You may have to exit and restart Firefox.

---

### Post by daniell59 on 2010-05-16
> **mgmiller said:**
> In Firefox, (namoroka) click on Edit > Preferences and go to the Applications tab.  Scroll down till you see "mailto" on the left side.  On the right side will be the mail program it's associated with.  The default is evolution.  Click the down arrow to the right and you should get a list of the mail programs, just select thunderbird, or if it's not listed, try "Use Other" and browse to it.  You may have to exit and restart Firefox.

Already did that with no results.

---

### Post by mgmiller on 2010-05-16
That's weird.  Have you tried exiting all instances of Firefox and Namoroka and logging off and back on to your desktop since you made the change in the browser?  Have you also tried making the change in Firefox 3.5 as well as Namoroka?

---

### Post by EssexEagle on 2010-05-16
> **daniell59 said:**
> Already did that with no results.

So what happens when you try to send a link?  Nothing at all, or do you get an error message?

---

### Post by EssexEagle on 2010-05-17
Actually there's several threads on this with some proposed solutions.  Take a look through these: [http://www.google.co.uk/search?q=+site:ubuntuforums.org+firefox+%22send+link%22](http://www.google.co.uk/search?q=+site:ubuntuforums.org+firefox+%22send+link%22)

---

