---
title: "Eclipse not showing documentation with OpenJDK"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by alphaakenny1 on 2009-01-07
I have openjdk-6-doc and all the other requirements installed, but in Eclipse no documentation shows when hovering over anything.  I even tried to change the prefences:

Window --> Preferences --> Java --> Installed JREs

Then I select java-6-openjdk and select Edit.

I pick /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar and click Javadoc Location.

I put file:/usr/share/doc/openjdk-6-doc/api/ in the Javadoc location path, but this cannot be validated because the package-list file is missing.  But in reality there is a file there (package-list.gz), which is an archive of the package-list file.  So I extracted it but still no documentation.  What am I doing wrong?  Thanks.

---

### Post by aasdfasdfg on 2010-05-29
I don't like to revive dead threads, but I am offering this as a help to others with the same issue I had (since this is first hit in google search).
To the OP: even though you were merely posting a question, it worked like an answer to me.

[SIZE=3]Situation: Trying to generate pretty JavaDoc on my machine.[/SIZE]
For a while, I have been complacent with my JavaDoc not linking to any Java builtins, but today I decided to change that. After some research, this thread was the only helpful thing that came up. I was starting to give up (because it seemed like the OP was stuck too), until I realized his mistake.
[SIZE=2]
I followed the same process, with two modifications:[/SIZE]

[LIST=1]
[*]  Slightly different directory location on system
[*]  Changed location of documentation in two places, not one.
[/LIST]
 
[SIZE=2]In-depth Explanation:[/SIZE]

[LIST=1]
[*] I opened up synaptic and browsed to the package openjdk-6-doc, which luckily was installed. I opened up the list of installed file for this package, and after some scrolling noticed three things:
[LIST=1]
[*]I had the same directory as the OP (/usr/share/doc/openjdk-6-doc/api/)  present on my syste
[*]It was empty
[*]However, there was another populated api directory: **/usr/share/doc/openjdk-6-jre-headless/api/**
So, in the relevant places, I used this directory instead (and made sure  to put file:/). Eclipse was able to verify it both times.
[/LIST]
 
[*]The OP described making the changes in the following location:
Window --> Preferences --> Java --> Installed JREs
As noted, this changes the preferences for when you hover over system  classes and the documentation window pops up. I wanted to do more - to  be able to generate links to system classes from within my JavaDoc. To  make this additional change is really straightforward, but I am  mentioning it in case it helps others. Go to:
Project --> Generate JavaDoc...
as you normally would when generated a JavaDoc, but instead of just  clicking Finish immediately, go on to the next screen. There, you should  see a list of jars that are all deselected, and will be followed by  various URLs. Scroll down to rt.jar, click Browse..., and change the URL  to say the same file location as in part (1).
[/LIST]

---

### Post by antiflag1980 on 2011-06-10
Thanks, this was driving me nuts. Your method works perfectly.

---

