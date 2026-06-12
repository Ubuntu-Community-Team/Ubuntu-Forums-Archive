---
title: "No-Interactive Bash User adding"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by sankarv on 2010-08-27
Hi

I just cameu with a wrapper to avoid manual intervention of setting password after useradd when asking for it in passwd command in linux in bash, however I am not sure whats the mistake its not working,... plz help/....

The last argument to the script is actual password and it need to be entered automatically when asked "New Password:" in passwd cmmand for that user created, after when the useradd command is given, condition being I should not user expect or other interactive tools other than bash.

```
$ cat test.sh
#get args
newargs=$*
#get last arg which is passwd
password=${newargs##* }
echo "PW:$password"
#form newlist of args excluding passwd
newargs=${newargs%$password}
echo "NA:$newargs"
#get last arg which is now username
username=${newargs##* }
echo "UN:$username"
newargpass="passwd $username"
#form actual command
eval "useradd $newargs"
(echo "echo $password")|eval $newargpass
$ 
```


The output is:

Shell # ./useraddnew -d /home/testuser testuser pass1234
PW:pass1234
NA:-d /usr/pkg/home/testuser testuser 
UN:
Changing local password for root.
New password:


Don't know why its not capturing username or setting the value passed on through echo in last step for password, please help.... thankx in advance....

---

