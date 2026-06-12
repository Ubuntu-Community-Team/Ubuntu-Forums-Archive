---
title: "version creating tool?"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by ja660k on 2009-05-30
hey guys,

is there a application that will make incremental versions of the applications i develop?

say if i have a directory tree 
and anytime i edit something within that directory tree the application creates a new version of what ive developed?

i know it sounds kinda ambiguous but any point in the right direction would help =D

---

### Post by QIII on 2009-05-30
What development platform are you using?  

Are you using an IDE like Netbeans or kdevelop?

If you are interested only in maintaining a record of source code changes, there are any number of applications and add-ins in most IDEs for that.

If you are saying you want a complete functional executable file and keep it somewhere separated from previous versions, create a new folder and build your application into that folder.

---

### Post by ja660k on 2009-05-30
i've come to like geany, 
but i sometimes use vim and stuff like that, i hate bloated IDE 

sorry, but yeah something like that would be great, having version backups and not having to use an ide like netbeans or eclipse

and no, its not executable file, its a java application, not a jar but a directory tree of .java and .class files

---

### Post by QIII on 2009-05-30
This is really not a Java forum, and this conversation probably doesn't belong here.  It would be best to take your question elsewhere, now that I think about it.

So, as my final parting words:

Netbeans is Sun's "official" Java (Sun, by the way) development environment.

IDEs are "bloated" for a lot of good reasons.

Like ease of debugging, tools for performance evaluation, detecting memory leaks, auto completion, alerting you to unused imports, detecting undeclared variables before you try to build, source code versioning ...

I go a ways back in the development game.  I started in the days when I carried a box of punch cards to send simple instructions over an accoustical coupling device to a mainframe at a university or a government agency.

Horse and buggy days.

I do woodworking when I have spare time.  Sometimes using hand tools to make furniture is satisfying.  It is not very efficient.

Productivity is key.  If you want to get your deliverables to your client on time, a conestoga is not the best way to go.

Just my humble opinion.

Anyway, what you are looking for may exist.  But why not use something already built into an integrated development environment.

If you don't build, you still have all the .java and .class files.  Just leave them in the directory where you last did what you wanted, make a new directory, copy the files there and point your project there from your IDE to make changes.

But if you are married to the idea of using Vim or Emacs or something like that, you could kludge the whole thing by copying the directory *in toto* and just open the files in the new directory in your text editor.

---

### Post by lovinglinux on 2009-05-30
> **QIII said:**
> This is really not a Java forum, and this conversation probably doesn't belong here.  It would be best to take your question elsewhere, now that I think about it.

The OP is not asking about Java development, but about a versioning system. I don't see any problem posting here. Nevertheless, the OP would probably get more useful replies in the [Programming](http://ubuntuforums.org/forumdisplay.php?f=39) Talk forum.

@ ja660k

I think you want something like subversion and esvn.

```
sudo apt-get install subversion esvn
```

With subversion, you have a repository for your application that stores the differences between each version of the files on your working directory. Every time you edit some files you can commit the changes to the repository or revert them to the previous version. Each commit has a number and you can add descriptions of the changes. You can then revert the files to any number version, compare them with diff and edit the files manually. It is a must have setup for any developer.

The esvn is a gui for subversion. You can find a complete manual at [http://zoneit.free.fr/esvn/html-docs/index.html](http://zoneit.free.fr/esvn/html-docs/index.html)

You might also like meld, which is a graphical comparing tool. It can compare directories or single files.

```
sudo apt-get install meld
```

---

### Post by AnRa on 2009-05-30
Try [Bazaar](http://bazaar-vcs.org/) ([click here to install](apt://bzr)).

---

### Post by ja660k on 2009-05-30
> **QIII said:**
> This is really not a Java forum, and this conversation probably doesn't belong here.  It would be best to take your question elsewhere

it would be best.. if you read before you jump into a reply :D

and thankyou for your help
subversion esvn was exactly what i need

---

### Post by QIII on 2009-05-30
> **ja660k said:**
> it would be best.. if you read before you jump into a reply :D

and thankyou for your help
subversion esvn was exactly what i need

I wasn't trying to be pissy.  Honestly.

And I use subversion for source code versioning.

Just sayin' ... as someone said above ... there are other forums in the Ubuntu playground.

But I accept your chastisement ...

---

