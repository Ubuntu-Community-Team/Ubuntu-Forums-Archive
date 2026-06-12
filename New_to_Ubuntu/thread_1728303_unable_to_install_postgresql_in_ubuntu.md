---
title: "unable to install postgresql in ubuntu"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by nkdnkd on 2011-04-13
hi all,
I am trying to install postgresql db for using with metasploit on my ubuntu 10.10 instln.
I am using the following guide :-
> [http://dev.metasploit.com/redmine/projects/framework/wiki/Postgres_setup](http://dev.metasploit.com/redmine/projects/framework/wiki/Postgres_setup)
I however, could not finish the step with installing libpq-dev
    sudo apt-get install libpq-dev
it complains about certain dependencies which are unresolved.
I tried out the synaptic and all the repositiories are added incl the mediubuntu !
Any ideas please
thanks in advance
nishith

---

### Post by josephmills on 2011-04-13
try this [http://dev.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu](http://dev.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu)

---

### Post by josephmills on 2011-04-13
ok I just installed it right now what you have to do is..
1) download the unix version [http://www.metasploit.com/download/](http://www.metasploit.com/download/)
2) get the Dependencies ```
$ sudo apt-get install ruby libopenssl-ruby libyaml-ruby libdl-ruby libiconv-ruby libreadline-ruby irb ri rubygems

```
then ```
sudo apt-get install subversion
```
then ```
sudo apt-get install build-essential ruby-dev libpcap-dev
```
3) take the downloaded file (framework-3.6.0.tar.bz2)from step one and move it to your desktop 
4) right click on the tar package (framework-3.6.0.tar.bz2) that you downloaded and moved to your desktop and click extract here 
5)after extracted open msf3 then open what ever package you like would like msfgui by left clicking on it then run it from the terminal 
6) have fun 
hope that this helps

---

### Post by nkdnkd on 2011-04-14
thanks for the inputs.
But I think I need to clarify the issue a bit further ;-
I am actually having difficulties with libpq-dev installation during installing of postgres for the metasploit .
how can I install the postgres without the dependency errors - it is rather strange that it says the dep won't be resolved ! I think I am missing some particular repo ?!?!? 
plz clarify
thanks again
nishith

---

### Post by SeijiSensei on 2011-04-14
You can install libpq-dev directly with 

```
sudo apt-get install libpq-dev
```

---

### Post by nkdnkd on 2011-04-14
> You can install libpq-dev directly with 
The dependency errors ?!?! are still there I tried that out
any more ideas
thanks
nishith

---

### Post by SeijiSensei on 2011-04-14
How about 

```
sudo apt-get update
sudo apt-get -f install libpq-dev
```

Sometimes a "sudo apt-get upgrade" in between those two can help, though I'd try without that first.

---

### Post by josephmills on 2011-04-14
please copy and paste all things, well trying to get that lib thanks

---

### Post by nkdnkd on 2011-04-18
I get the following errors :-
> nishith@nishith-Aspire-4720:~/Desktop/.Security$ sudo apt-get install libpq-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libpq-dev : Depends: libssl-dev but it is not going to be installed
             Depends: libkrb5-dev but it is not going to be installed
E: Broken packages

How to resolve these
thanks in advance
nishith

---

### Post by josephmills on 2011-04-18
The following packages have unmet dependencies:
libpq-dev : Depends: libssl-dev but it is not going to be installed
Depends: libkrb5-dev but it is not going to be installed
E: Broken packages

---

### Post by nkdnkd on 2011-04-19
I could understand that ... but trying to install these also give further dependencies and complain they won't be installed. I think I am missing a repo here
any clues
thanks
nishtih

---

### Post by josephmills on 2011-04-19
> **nkdnkd said:**
> I could understand that ... but trying to install these also give further dependencies and complain they won't be installed. I think I am missing a repo here
any clues
thanks
nishtih

try ```
$ sudo apt-get install ruby libopenssl-ruby libyaml-ruby libdl-ruby libiconv-ruby libreadline-ruby irb ri rubygems
``` 
then 
```
sudo apt-get update
```

---

### Post by Locke_99GS on 2011-04-19
```

sudo apt-get install -f
sudo apt-get update; sudo apt-get install libkrb5-dev

```

Then try to continue with the rest of your install process.

---

### Post by nkdnkd on 2011-04-19
the outputs are as under :-
> nishith@nishith-Aspire-4720:~/Desktop/.Security$ ***sudo apt-get install ruby libopenssl-ruby libyaml-ruby libdl-ruby libiconv-ruby libreadline-ruby irb ri rubygems***
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libruby' instead of 'libopenssl-ruby'
Note, selecting 'libruby' instead of 'libyaml-ruby'
Note, selecting 'libruby' instead of 'libdl-ruby'
Note, selecting 'libruby' instead of 'libiconv-ruby'
Note, selecting 'libruby' instead of 'libreadline-ruby'
Note, selecting 'ruby' instead of 'irb'
libruby is already the newest version.
ri is already the newest version.
ruby is already the newest version.
rubygems is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.

> nishith@nishith-Aspire-4720:~/Desktop/.Security$ ***sudo apt-get update***
Ign file:  Release.gpg
Ign file:/var/my-local-repo/  Translation-en                                   
Ign file:/var/my-local-repo/  Translation-en_IN                                
..............                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages
Fetched 72B in 16s (4B/s)
Reading package lists... Done

[email]nishith@nishith-Aspire-4720:~/Desktop/.Securi[/email]ty$ ***sudo apt-get install -f***
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
> nishith@nishith-Aspire-4720:~/Desktop/.Security$*** sudo apt-get install libkrb5-dev***
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libkrb5-dev : Depends: krb5-multidev (= 1.8.1+dfsg-5) but it is not going to be installed
E: Broken packages
 

BACK TO SQUARE ONE......THIS THING IS JUST NOT WORKING!
NISHITH

---

### Post by Locke_99GS on 2011-04-19
It tells you where the problem is. Try installing that package (krb5-multidev) and it should tell you what dependencies it cannot resolve.

---

### Post by josephmills on 2011-04-19
do you all ready have framwork3 installed ? can you open mfsconsole? or msfgui?

---

### Post by josephmills on 2011-04-19
also what repos do you have open?

---

### Post by josephmills on 2011-04-19
more pics

---

### Post by nkdnkd on 2011-04-22
> do you all ready have framwork3 installed ? can you open mfsconsole? or msfgui?
Yeah and it works fine. Just that I want to use the db_nmap , db_autopwn etc.
I have the following repos :-
Medibuntu, canonical, multiverse.
BTW I tried out installing the other dependencies too.......but they come with more and more deps..... like the dependency hell !
I tried installing the failed deps using Synaptic and Ubuntu software centre too.....
It seems like a repo related problem please let's think in that line.
thanks
nishith

---

### Post by nkdnkd on 2011-04-23
a

---

