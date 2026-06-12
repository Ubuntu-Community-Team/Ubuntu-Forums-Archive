---
title: "Automated FTP Process?"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by driggins on 2008-01-02
Greetings,

I'm seeking a method to automatically upload a single file via FTP to my personal domain once a day. Conceptually this sounds very straight-forward to me, but I'm unsure how to proceed. I'm not familiar with command-line FTP or writing scripts - two skills that I'm guessing would need to be employed for this solution. Is anyone willing to walk me through this process?

Thanks,
daryl

---

### Post by mips on 2008-01-02
> **driggins said:**
> I'm not familiar with command-line FTP or writing scripts - two skills that I'm guessing would need to be employed for this solution. Is anyone willing to walk me through this process?

That would be the way to do it. I'm no good at scripts though.

---

### Post by sdide on 2008-01-02
The following script, lets put it in a textfile in your bin directory and call it ftp_auto.sh should do the job, you just have to replace everything in the <...> brackets with your relevant information:
#=============================
#!/bin/sh
HOST=<DNSname_or_ip_of_your_ftp_server>
USERNAME=<your_username_on_ftp_server>
PASSWORD=<your_password_on_ftp_server>

cd <path_to_where_file_is>
ftp -n $HOST <<EOD
quote USER $USERNAME
quote PASS $PASSWORD
cd <path_to_where_file_should_be_on_remote_machine>
put <file>
quit
EOD
exit 0
#================================

Since your password is in clear text, you might not want to make this file readable for others, and also it should be executable for you, so.

$ chmod 700 ftp_auto.sh

To execute the scipt once a day automatically - use your crontab.

$ crontab -e
this will spawn default Nano editor I think.

add the line 

0 23 * * *       $HOME/bin/ftp_auto.sh >> $HOME/tmp/ftp_auto.log 2>&1

Which should try to execute the script every time the hour hits 23. that is once every day at 23:00 hours. Provided the machine is turned on that is. :)

---

### Post by kevdog on 2008-01-02
I understand everything except the EOD.  Can you explain this part?

---

### Post by sdide on 2008-01-02
Its a shell thing. "Here Documents" .

See  $ man bash 
and search for "Here Documents"

quote: "This  type  of  redirection  instructs  the shell to read input from the current source until a line containing only word (with no trailing blanks) is seen."

Its very handy.

So I could have used "Monkey" istead of "EOD".

---

### Post by mips on 2008-01-02
How would one specify a binary or text file ?

---

### Post by sdide on 2008-01-02
to specify a binary file, you just type "bin" in the ftp session.
to specify ascii, you type "ascii".

You can do that in the script after username and password lines, and before 
the put file.

---

### Post by driggins on 2008-01-03
sdide,

This is great. Thanks for taking the time to spell it out for me!

I've created the script, which looks like:
> #!/bin/sh
HOST=<MY DOMAIN>
USERNAME=<MY USER NAME>
PASSWORD=<MY PASSWORD>

cd <path_to_where_file_is>
ftp -n $HOST <<EOD
quote user $USERNAME
quote $PASSWORD
cd <public_html/campbrain/>
put </media/data/Shared/CampBrain/chestnut_ridge2008.mdb>
quit
EOD
exit 0

I tested the FTP commands and altered the script accordingly. Specifically, I changed "USER" to "user" and omitted "PASS".

To test the script, I'm using:
> sudo sh /home/daryl/Desktop/upload_campbrain.sh

I receive the following after executing the above line:
> /home/daryl/Desktop/upload_campbrain.sh: 2: Syntax error: newline unexpected

Any ideas?

---

### Post by sdide on 2008-01-04
Its because you kept the "<" and ">"'s in the script.
You need to remove them.

HOST=<your_ip> usually means, 
replace "<your_ip>" with an ip address, eg

HOST=10.3.5.6

The goes for each line where variable values are enclosed in "<" and ">"

The thing is that the shell interprets that you want to redirect things.

---

### Post by driggins on 2008-01-10
Okay, they "<" and ">" are now gone. Here's the current script:
> #!/bin/sh
HOST=my host name
USERNAME=my user name
PASSWORD=my password

cd /media/data/Shared/CampBrain/
ftp -n $HOST <<EOD
quote user $USERNAME
quote $PASSWORD
cd public_html/campbrain/
put /media/data/Shared/CampBrain/chestnut_ridge2008.mdb
quit
EOD
exit 0

After executing with "sudo sh /home/daryl/Desktop/upload_campbrain.sh" I receive the following:
> Syntax error, command unrecognized.
Login first, then I might let you do that.
Login first, then I might let you do that.
Login first, then I might let you do that.
ftp: bind: Address already in use


I attempted to run the commands one at a time to determine the syntax error, but didn't have any luck. Is anything obvious to you?

Thanks,
daryl

---

### Post by KCPokes on 2008-01-10
Nothing jumps out as being obvious.  Couple things.

```

HOST=my host name

```

You are using hostname and not IP?  Just to be sure, your hostname does resolve in DNS, correct?  You'll need it to be a fully qualified hostname thats resolves in DNS or your hosts file.  

```

ftp -n $HOST <<EOD
quote user $USERNAME
quote $PASSWORD
cd public_html/campbrain/
put /media/data/Shared/CampBrain/chestnut_ridge2008.md b
quit
EOD

```

Another spin on the same thing, that you might try if you continue to get errors:

```

ftp -n $HOST <<EOD
user $USERNAME $PASSWORD
cd public_html/campbrain/
put /media/data/Shared/CampBrain/chestnut_ridge2008.mdb
bye
EOD

```

Same thing, but another approach at authenticating as it seems you are not getting logged in before.  That may be because of connection, due to DNS resolution, but not sure.

---

### Post by tmcmulli on 2008-01-13
There's another way to do this.  Use the .netrc file.  Your system has a file in your default directory called .netrc.  You can add a macro, and call that macro when you want to upload your file.  I've gone through scripts, and I could get them to work, but automating the upload became tricky.

here's the files I use now:

sudo gedit ~/.netrc

```
machine 192.168.1.50
login user
password password

macdef backupfiles
prompt off
lcd /backup
cd 200gb/timbuntu64
mput *.tar

```

You can change the "mput *.tar" line to be any filename you want.

Then you can test the macro by this line:   echo "$ backupfiles" | ftp 192.168.1.50

This will automatically call your macro, login and upload the file to the correct location.

To get this to automatically run every day, edit the crontab jobs.  This is done via:

crontab -e

This file allows you to execute tasks or scripts and schedule the time they will execute.  Mine looks like this:

15 1 * * * echo "$ backupfiles" | ftp 192.168.1.50

This means it runs at 1:15 am every morning.

Tons of information on the forums here about crontab and cron.

Tim

---

### Post by sdide on 2008-01-16
```
#!/bin/sh
HOST=my host name
USERNAME=my user name
PASSWORD=my password

```

If you have written this literally - it will fail. Because your host is not called
"my host name", etc. Your host is an ip address or a FQDN, username and
password should not contain spaces.

IP address example; 10.3.5.6
FQDN example; [www.google.com](www.google.com)

Besides if you want to set variable with spaces in it, you need to enclose
it in quotations. Hence if you want to assign to the variable VAR the value 
of my full name. 

The line below will fail:
```
$ VAR=Soren Dideriksen
```
whereas this line below will work:
```
$ VAR="Soren Dideriksen"
```

---

### Post by driggins on 2008-01-17
When pasting the contents of the script, I replaced my actual host and user names with "my user name" in order not to share that info with the world at large. Thanks for the pointer, though.

---

