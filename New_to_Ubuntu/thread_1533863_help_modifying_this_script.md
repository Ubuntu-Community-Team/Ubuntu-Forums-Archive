---
title: "help modifying this script"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-07-18
just learning so bear with me

here is a script

#!/bin/bash
sudo su bleachbit
sudo shutdown -r now

how would i modify it so it runs without me having to type in my password is there a delay command and maybe a way of entering my password in the script. all i am doing is emptying some temp files etc and rebooting/tks

---

### Post by YesWeCan on 2010-07-18
I think you can pipe the password into sudo in this form:

echo <password> | sudo -S <command>

---

### Post by rburkartjo on 2010-07-18
tks yes but have no idea how to do

---

### Post by Windows Nerd on 2010-07-18
I think he means do this to run the two commands with sudo privliges without having to type your password:

```
#!/bin/bash
echo <password> | sudo -S bleachbit 	
echo <password> | sudo -S shutdown -r now
```

I am no expert with bash scripting, so if YesWeCan can check this over you should be good to go.

By the way, the way that script looks, you are running bleachbit, but trying to shutdown the system at the same time, again, I am no expert, and am not sure if Bash waits to make sure the command in one line is completed before going onto the next.

Scott

---

### Post by mcphargus on 2010-07-18
You can add NOPASSWD to your sudoers file on a per-command/per-user basis. I would say that that can be a security risk, but writing your password into a script isn't the most secure thing to do either :)

Check out how here: [http://www.linuxquestions.org/questions/linux-general-1/sudoers-file-no-password-615334/]("http://www.linuxquestions.org/questions/linux-general-1/sudoers-file-no-password-615334/")

---

### Post by mcphargus on 2010-07-18
> **Windows Nerd said:**
> 
By the way, the way that script looks, you are running bleachbit, but trying to shutdown the system at the same time, again, I am no expert, and am not sure if Bash waits to make sure the command in one line is completed before going onto the next.

You can make sure the command is finished by combining it with &&. 

```

echo <password> | sudo -S bleachbit && echo <password> | sudo -S shutdown -r now

```

And you have to use -S option with sudo to make any of the above work.

---

### Post by YesWeCan on 2010-07-18
> **Windows Nerd said:**
> I think he means do this to run the two commands with sudo privliges without having to type your password:

```
#!/bin/bash
echo <password> | sudo -S bleachbit 	
echo <password> | sudo -S shutdown -r now
```

I am no expert with bash scripting, so if YesWeCan can check this over you should be good to go.

By the way, the way that script looks, you are running bleachbit, but trying to shutdown the system at the same time, again, I am no expert, and am not sure if Bash waits to make sure the command in one line is completed before going onto the next.

Scott

Yep, that's what I was implying. I should not imply I should be explicit, sorry.
The -S option tells sudo to receive the password from stdin (standard input) and the echo provides the password to stdin.

I am not sure about whether it waits for the first command to finish or not. I guess it does but I have poor knowledge of shell scripting. This may clinch it - only reboot if the first completes successfully. But you'd have to test this works for yourself.

```
#!/bin/bash
if
  echo <password> | sudo -S bleachbit 	
then
  echo <password> | sudo -S shutdown -r now
fi

```

---

### Post by rburkartjo on 2010-07-20
window,mc and nerd tks all those worked great and yes the first one worked great. okay next step how to i make this script run at shutdown. no i have to put it in crontab.but where and how/tks

---

### Post by nmaster on 2010-07-20
> **mcphargus said:**
> You can add NOPASSWD to your sudoers file on a per-command/per-user basis. I would say that that can be a security risk, but writing your password into a script isn't the most secure thing to do either :)

Check out how here: [http://www.linuxquestions.org/questions/linux-general-1/sudoers-file-no-password-615334/](http://www.linuxquestions.org/questions/linux-general-1/sudoers-file-no-password-615334/)

+1

the rest of you are crazy.  it is a terrible idea to store your password in a text file like that.  plus, if you change the password the script will no longer work properly.  you need to edit the sudoers file.

---

### Post by nmaster on 2010-07-21
ya know... if you're going to reboot anyway, you might as well just drop into root and then run the commands.  

```

$ sudo su
[sudo] password for user: 
root# bleachbit && shutdown -r now

```or maybe keep the bleachbit and reboot in a script so you can run them with one command. also, this prevents you from having to edit the sudoers file.

---

### Post by CaptainMark on 2010-07-21
theres the sleep command if you want to put a manual pause in, for a 20 second delay between two commands ```
<command1> &&sleep 20&& <command2>
```

---

### Post by debjit_bis08 on 2010-07-21
Add this to the suodoers file using the "sudo visudo" command:

$ your_username ALL=(ALL) NOPASSWD: path_to_script

then change the owner of the file to root:root

$ sudo chown root:root path_to_script

next change the permissions to --wx--x--x (311)

$ sudo chmod 311 path_to_script

now no one except the root (for which password has to be entered) can read or write the file and you can run the file without the password.

When testing this use "sudo -k" to invalidate the user timestamp.

---

### Post by rburkartjo on 2010-07-21
everyone tks for all your help you have answered everything apppreciate it

---

