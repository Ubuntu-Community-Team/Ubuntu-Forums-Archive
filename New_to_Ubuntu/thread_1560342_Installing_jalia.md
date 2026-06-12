---
title: "Installing jalia"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by ep1centre on 2010-08-24
Hello,


I am trying to install jalia (the accounting software) however the intalation notes are somewhat vague besides the point that I really don't know what I'm doing when it comes to manually installing programs (I believe the term is compileing software?!?)

I'm quite good with this sort of stuff but not knowing how the Linux structure works makes things a tad harder so can anyone please help me on a step by step basis?

Thank you.

---

### Post by davidmohammed on 2010-08-24
... so what happens when you follow the [installation guide]("http://jalia.sourceforge.net/Suse_Installation_Guide.htm")?

---

### Post by Paul820 on 2010-08-24
If you open the **Ubuntu Software Centre** and search for accounting, there are a few that come up. Are any of them useful? It would save you from compiling from source.

---

### Post by ep1centre on 2010-08-24
> **davidmohammed said:**
> ... so what happens when you follow the [installation guide]("http://jalia.sourceforge.net/Suse_Installation_Guide.htm")?


Well to start with to be honest that's not the guide I have, the one I have its ... Well like I said vague, that one seems much better, the only thing I see there is that mentions SuSe and Redhat, I assume the steps are the same for Ubutu or else you wouldn't have recomended it to me?

Thank you


> **Paul820 said:**
> If you open the **Ubuntu Software Centre** and search for accounting, there are a few that come up. Are any of them useful? It would save you from compiling from source.

I tried that however the programs that come up are quite basic... They're all aimed at personal use, I'm looking for something a little more advanced!

---

### Post by Paul820 on 2010-08-24
Is it the one from sourceforge? If it is you don't need to compile it you just follow the instructions in the readme. According to that you need to install the java SDK, which is in the repositories and then get the PostgreSQL from their website and install it, then it's step by step from there.

---

### Post by ep1centre on 2010-09-03
hello, its been a few days now (i've had other priorities) but now its time i came back to the issue of getting this program installed and running.

ok so far i've installed something called JDK (generic java development kit) more or less as per your last instructions
then i went to install PostgreSQL and when i followed the links for what i thought was gonna be a download link for a ubuntu installer program, it just said to install it making use of the apt feature, which i'd assumed it was gonna be something llike:

sudo apt get PostgreSQL

but no luck there - i know the command is wrong but unfortunatly i'm a linux newby

can i please get some more help on this?

thank you.

---

### Post by ep1centre on 2010-09-03
Based on this how to can someone add notes/write up a proper noob's how to for this installation please? it says things like "from the root of *** run the compile command" well that's all good if you know how to put a command's syntax together which i don't i dont even know how to navigate myself into the root folder of this program using terminal... can anyone please help me with this?




Jalia How-To
============
Jalia uses JasperReports library for report generation. The required libraries 
are available in the lib directory of the project's root directory.

To use jalia, you must have PostgreSQL 7 or higher as the database and you must 
have java JDK 1.3 or higher.  -- [COLOR=RoyalBlue]I think i've installed both java jdk and porsgreSQL using synaptic packet manager, though i'm not sure.[/COLOR]

Make sure you have PostgreSQL database installed. Goto 
"http://www.postgresql.org" for PostgreSQL download. -- [COLOR=RoyalBlue]this didn't help as it just tells you to "use the built in apt feature to install the program"[/COLOR]

Make sure you have jdk1.4 or jdk1.5 installed, and add the directory which 
contains the java and jar executable into your system path. [COLOR=RoyalBlue](not sure what that means but i take it its just install it?)[/COLOR] Go to 
"http://java.sun.com/" for JDK download if you didn't install it yet.In order to 
compile & run the application, you need to have JDK installed in your system. 

1) Compile the Source Files
---------------------------
Having downloaded & installed JDK in your system, execute the "misc/compile" 
command from the project's root directory to compile all java source files. [COLOR=RoyalBlue]again this is what i meantioned earlyer i take it that means open terminal, navigate to the root directory OF the program i'm trying to install NOT the computer's root folder and then run the command to compile/install the program, though even if that's correct i have no idea on how to do either, run the compile command or even navigate to that particular folder.[/COLOR]

2) Setup the Jalia DB
---------------------
Jalia requires PostgreSQL database. 

2.1) After setting up the postgreSQL server, copy the "jaliadb.gz" file from 
project's root directory to the postgres home on the postgreSQL server. [COLOR=RoyalBlue]right where the hell is the porsgre's server... i haven't done nothing but install a couple of packages from the packet manager, there's no program running there's no "programs" folder that i could just browse and paste said file into... doesnt make sence to me.[/COLOR]

2.2) Login to the postgreSQL server as postgres user & create a database by name 
jaliadb [COLOR=RoyalBlue]- again that's all very well if i knew where/how/what this so called server is.[/COLOR]

2.3) Execute the following command :
cat jaliadb.gz | gunzip | psql jaliadb [COLOR=RoyalBlue]- take it once logged in there is a command prompt somewhere to run said command, or is this to be ran in the OSs terminal? whoever wrote this obviously looked at it from an outside perspective.... not![/COLOR]

2.4) Change the DB_URL property in the 
"com/itcs/jalia/server/JaliaDB.properties" file from the project's root 
directory to the respective postgreSQL server IP
For eg.:
DB_URL           = jdbc:postgresql://xxx.xxx.x.xx/jaliadb [COLOR=RoyalBlue]- i dont even know where to start on this one, just dont understand it.[/COLOR]

3) Run Jalia [COLOR=RoyalBlue]- hopefully this is just double clicking on an icon on the desktop.[/COLOR]
------------
From the project's root directory execute the command "jalia" which should 
launch the Jalia application [COLOR=RoyalBlue]- again makes no sence, is this an added note to point 3 or just a random afterthought.


[COLOR=Black]i know that I'm really not the brightest linux user but i know that my general PC skills are well above average which is scary, if i can't figure out a lot of this stuff how on earth are most people soposed to.

just as a side note and when it comes to this i really don't know much, but how hard would it be for whoever creates the program to create some sort of an installer that just took all these steps automatically? just seems like a program which could be an absolute breeze to use its in fact a nightmare because of all this complicated set up process.
[/COLOR][/COLOR]

---

### Post by ep1centre on 2010-09-05
Anyone?

Please!

---

### Post by ep1centre on 2010-09-06
Bump

---

### Post by Paul820 on 2010-09-08
Well,i tried. I just can't get it to work. I installed the jre and jdk and built the jalia program but that had some sort of warnings about items being deprecated. I installed postgresql and can't find it anywhere, even when typing 'postgresql' or 'postgreqsl-8.4', the system hasn't got a clue where it is. I have never used the program so i really don't know how to run that. I have looked for help but there are questions on sourceforge people are asking which are going unanswered. The documentation as you have pointed out for jalia is pretty crap.

I did a search on google for accounting software and found this [http://www.ubuntugeek.com/install-gnucash-financial-accounting-software-in-ubuntu.html]("http://www.ubuntugeek.com/install-gnucash-financial-accounting-software-in-ubuntu.html") which says it's
'GnuCash is personal and small-business financial-accounting software' which i believe is what you are looking for. All you have to do to get that running is 'sudo apt-get install gnucash'

Sorry i couldn't help you further.

---

### Post by ep1centre on 2010-09-08
Thank you very much, I too have managed to get a more-Linux-switched-on friend to help me with this issue and he had no luck getting anywhere with this, After a lot of reading it seems that the program is a bit old... If no one's working on it then perhaps it's not a good choice anyway.

I tried gnucash It seems ok even if a tad complicated but it's probably the one I'll go for it's just a shame that I can seem to be able to add "notes" for "jobs" if I was able to then this would make it perfect for me as I would also be able to use it as a basic repair track system.

As per my friends suggestion before making a decision on what to use, try using turbo cash via wine.

Anyway thank you again for all your help it's very much appreciated.

---

