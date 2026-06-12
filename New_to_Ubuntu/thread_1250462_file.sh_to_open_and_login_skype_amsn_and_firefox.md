---
title: "file.sh to open and login skype amsn and firefox"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by xkman on 2009-08-26
[B]Hi, how do I make a file.sh to open my email, Skype and AMSN loging in?

I know how to chance permission with "chmod +x arquivo.sh"

I want to execute the following commands:

-open AMSN, user, password
-open SKYPE, user, password
-open FIREFOX, call GOOGLE MAIL, login, password

I was successfull in opening the programs individually, but not in sequence.
To open an log in in Gmail i did:[/B]

[I]echo "Firefox" ; firefox [http://mail.google.com;](http://mail.google.com;)

 echo "User: " ; #USER
 read login
 echo "Pass: " ; #PASSWORD
 read pass

curl -u $login:$pass
[/I]
[B]That opens the Firefox and log me in
But I have several problems. When I open the AMSN or SKYPE I don't know how to login after the first command is executed (open program) the SHELL "stops", no commands are  accepted anymore. (I'm newbie, dunno why the prompt doesn't accept commands anymore)[/B]
[B]Would be also great if I could use a password to allow the execution of the Script. The problem is not letting anyone open the file to read the passwords in the SCRIPT.
I thought something like:
[/B]
IF 
password=1234

THEN 
"keep executing Script"

ELSE 
echo "false password"
exit

[B]But that doesn't make the file safe, since it would be easily openned with an text editor.

Anyone?

Thank You!!![/B]

---

### Post by Liolikas on 2009-08-26
What you wrote until now is almost pure nonsense.
What you try to do is partially impossible at all.

I suggest to read this page first:
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by xkman on 2009-08-27
LOL
 
Sorry. 
I thought that Shell-Script were more powerfull. 
I started reading the page, but in advance, would you say that it's not possible, at least, to make a "Shortcut" to open 3 programs?
 
Thank you.

---

