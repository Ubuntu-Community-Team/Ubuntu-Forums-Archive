---
title: "[SOLVED] Writing a script fo run a java program"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by wheelerrver on 2008-12-05
I am a n00b on this, so I hope my topic makes sense.  I have used the program Arachnophilia to work on web pages on my Windows computers in the past.  I discovered that the latest version is written in Java and it works in Ubuntu.  I followed the instructions in the program's home page at: [http://vps.arachnoid.com/arachnophilia/](http://vps.arachnoid.com/arachnophilia/) and the program runs fine using  the first step of the following instructions.  However, I do not know how to do the second step starting with the words "For convenience,.." or how to make a desktop icon for the script.  Any help appreciated.

The author's instructions are:

Open a command console (Linux: shell console), move to the Arachnophilia program directory, type "java -jar Arachnophilia.jar"
For convenience, this command can be made part of a shell script, and those using X windows can easily make a desktop icon.

---

### Post by Het Irv on 2008-12-05
Try right clicking on the desktop and click "Create Launcher", change the box where it says "Application" to "Application in Terminal".  In the command box type the "java -jar..." command.  I am not sure how to do a shell script... but this should get you to the same place.

---

### Post by jespdj on 2008-12-05
Just create a text file with one line in it, containing the command that you normally type in to run the program.

Save the file and make it executable:
```
chmod u+x scriptfile
```

I don't know Arachnophilia, but at first sight it looks a lot like Bluefish, which is in the Ubuntu repository (you can install it with Synaptic or with "sudo apt-get install bluefish").

---

### Post by niteshifter on 2008-12-05
> **Het Irv said:**
> Try right clicking on the desktop and click "Create Launcher", change the box where it says "Application" to "Application in Terminal".  In the command box type the "java -jar..." command.  I am not sure how to do a shell script... but this should get you to the same place.

Almost spot-on. What's missing you ask?

The path to the .jar file.

For example, if Arachnophilia.jar is in a folder called webtools in a user's home folder (for user "bob") then what goes into Launcher Properties window (the Command text box) is:

```
java -jar /home/bob/webtools/Arachnophilia.jar
```

---

### Post by Het Irv on 2008-12-05
> **niteshifter said:**
> Almost spot-on. What's missing you ask?

The path to the .jar file.

For example, if Arachnophilia.jar is in a folder called webtools in a user's home folder (for user "bob") then what goes into Launcher Properties window (the Command text box) is:

```
java -jar /home/bob/webtools/Arachnophilia.jar
```
ah, thanks I didn't think about that

---

### Post by wheelerrver on 2008-12-05
I appreciate all the help so far.  I have been able to get the program to run using the java -jar command line.  I will try the executable file route, but one question on that, do I replace the words scriptfile with the text file name when I type in the code?

"Save the file and make it executable:
Code:

chmod u+x scriptfile"


I will take a look at Bluefish, too.  Just used to Arachno and know its quirks.

---

### Post by wheelerrver on 2008-12-07
This problem is solved.  For any other real n00b like me, this is what I did using Ubuntu Intrepid.

I opened the text editor.  In that I typed the coding that I needed.

java -jar Arachnophilia.jar

that is all I put in the text file, although it appears I could add some descriptive info by putting a # in front of the info.

I saved the file to my home directory.

I tried the chmod command suggested above and it appeared to work.  I then went to my directory where the text file exists and right clicked on it and checked its properties.   I went to permissions for the file.  There is a check block there asking if I want it to be an executable file.  That was not checked, so I checked it.  

Now when I click on the text file in the directory, it gives me the choice of running it in terminal or displaying it (which means opening it in text editor).  When I click on running it in terminal, the program starts.

Incidentally, I looked at Bluefish and will try it, too.

---

