---
title: "BEAGLE and GMAIL: &quot;All Mail&quot; folder"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by Krevads on 2009-08-12
Hello everybody, i'm a novice user
I installed beagle today and tried to make it index gmail, but i couldn't get it to index the "all mail" folder... i can get it to index any other folder, but looks like "all mail" being two words is a problem, and it doesn't work 

i.e. 
```
beagle-config GoogleBackends GMailSearchFolder Inbox
```works, while
```

beagle-config GoogleBackends GMailSearchFolder All Mail
```doesn't work.

```
beagle-config GoogleBackends GMailSearchFolder "All Mail"
```doesn't work either 

is it possibile to make it work? what command should I use?

thanks everybody, and I hope this is the right section of the forums

---

### Post by nickzeff on 2009-10-15
I was just trying to work out the same thing... and I have solved it, if you are still interested.

"All Mail" is a subfolder of the special folder Google creates called "[Google Mail]". On _[this page of Gmail's online documentation]("http://mail.google.com/support/bin/answer.py?hl=en&answer=82367")_ and [_in the Beagle documentation_]("http://beagle-project.org/Live_GMail_Search"), it says the name is "[Gmail]" but that doesn't seem to work for me.

(I worked out the correct folder name by connecting Thunderbird to Google's IMAP service and seeing what folders appeared for me).

So the command which finally worked for me was 

```
beagle-config GoogleBackends GMailSearchFolder "[Google Mail]/All Mail"
```

---

