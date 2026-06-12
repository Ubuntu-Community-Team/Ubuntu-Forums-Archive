---
title: "[SOLVED] Meaning of #"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by gerreth on 2009-01-04
Hi,

While setting up my mailserver, i saw a lot of "#" in documents. Right i have to edit a document. 
In my ldap.conf i have to change
```
#BASE     dc=example,dc=com
```
to
```
#BASE     dc=something,dc=else
```
Do i have to remove the #? I think it sets parts in comment. If so, is this a general rule for all configuration files?


Thx
.
Gerreth

---

### Post by Tim Sharitt on 2009-01-04
# usually does denote a comment. However, in some configuration files, it isn't necessary to remove them for some settings (such as in grub's menu.lst).

---

### Post by scorp123 on 2009-01-04
> **gerreth said:**
> Do i have to remove the #? If you want that particular setting to be activated, then yes. Else it will be regarded as comment and you can change the line as much as you want: it will never ever become active.

---

### Post by gerreth on 2009-01-04
Thx :)

---

### Post by Kellemora on 2009-01-04
Hi garreth

Not mentioned is that you normally would NOT want to remove the pound sign from in front of COMMENTARY as it could mess things up royally.

For example:  A line may read (pound sign) This is command is needed to do whatever the command is for.

Under that you should see a command with a semi-colon in front of it ALSO meaning it's turned OFF, not read.
IF you need this command, you would REMOVE the semi-colon from in front of the command and it will be ACTIVATED the next time that SCRIPT is run.

Unlike Windows, you don't have to reboot after every change of something.  For example:  If you made a change in your smb.conf file, like added YOUR Workgroup name MYWORKGROUP behind the command WORKGROUP, so it would now read WORKGROUP = MYWORKGROUP.
Rather than rebooting you would type in Terminal
```
 sudo /etc/init.d/samba restart
```
and this will stop and restart samba.  Or from Root Terminal you would omit using the word sudo.

TTUL
Gary

---

### Post by The Cog on 2009-01-04
Completely off topic, but the # symbol is not an English pound sign. It has no meaning at all in English. I think it is an American "number" sign. An English pound sign looks like this: £ unicode value 163.

---

### Post by gerreth on 2009-01-04
> **Kellemora said:**
> Hi garreth

Not mentioned is that you normally would NOT want to remove the pound sign from in front of COMMENTARY as it could mess things up royally.

For example:  A line may read (pound sign) This is command is needed to do whatever the command is for.

Under that you should see a command with a semi-colon in front of it ALSO meaning it's turned OFF, not read.
IF you need this command, you would REMOVE the semi-colon from in front of the command and it will be ACTIVATED the next time that SCRIPT is run.

Unlike Windows, you don't have to reboot after every change of something.  For example:  If you made a change in your smb.conf file, like added YOUR Workgroup name MYWORKGROUP behind the command WORKGROUP, so it would now read WORKGROUP = MYWORKGROUP.
Rather than rebooting you would type in Terminal
```
 sudo /etc/init.d/samba restart
```
and this will stop and restart samba.  Or from Root Terminal you would omit using the word sudo.

TTUL
Gary

I restarted postfix and ldap
```
tail -f /var/log/syslog
/etc/init.d/postfix restart
/etc/init.d/slapd restart
/etc/init.d/courier-imap restart

```

It gave no errors, but the thing ain't working. I tried to link ldap to postfix, but I  have no idea thing is working.

Is their a way to check this?
I think i modded all necessary files...

When i run this:
```
telnet localhost 25
```
Connection succesfull, ok.
```
helo gerreth
```
```
mail from: me@gerreth.intern
rcpt to: other@gerreth.intern
data
Hi,
Test...
.

```

Gives this error :s

250 2.0.0 Ok: queued as 70EFF1234D

Thx

---

