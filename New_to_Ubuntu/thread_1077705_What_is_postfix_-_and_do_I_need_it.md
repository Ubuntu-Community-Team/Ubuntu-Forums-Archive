---
title: "What is postfix - and do I need it?"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by abyssius on 2009-02-22
I keep getting this error message, whenever I restart networking (/etc/init.d/networking restart). It doesn't appear in any of my logs - only when using dmesg. 

```
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
```

I found that I can also reproduce the error by issuing:
```

postfix reload
dmesg

```

I'm not aware of any problems caused by this error. What is postfix anyway and can I simply uninstall it?

---

### Post by rhcm123 on 2009-02-22
> **abyssius said:**
> I keep getting this error message, whenever I restart networking (/etc/init.d/networking restart). It doesn't appear in any of my logs - only when using dmesg. 

```
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
```

I found that I can also reproduce the error by issuing:
```

postfix reload
dmesg

```

I'm not aware of any problems caused by this error. What is postfix anyway and can I simply uninstall it?

Postfix is a email MTA and is not really nessecary if you don't plan to send/reccive emails.

It seems that your postfix installation is damaged. Run the following command to remove it.

```
sudo apt-get --purge remove postfix
```

---

### Post by abyssius on 2009-02-22
> **rhcm123 said:**
> Postfix is a email MTA and is not really nessecary if you don't plan to send/reccive emails.

It seems that your postfix installation is damaged. Run the following command to remove it.

```
sudo apt-get --purge remove postfix
```

I do use both thunderbird and evolution email clients, as I have several email addresses I use regularly. However, they both seem to work okay. I'll try your command and then re-install postfix to see what happens. Thanks for the reply.

---

### Post by rhcm123 on 2009-02-22
> **abyssius said:**
> I do use both thunderbird and evolution email clients, as I have several email addresses I use regularly. However, they both seem to work okay. I'll try your command and then re-install postfix to see what happens. Thanks for the reply.

No, postfix is a mail server. When you send emails via thunderbird and evolution, they logon to the remote servers (i'll use gmail as an example) and start an SMTP connection that downloads the mail from smtp.google.com to your local machine. Not to postfix.

Postfix is the actual server that your computer would connect to (it's one of them and the most common, but there are other MTA's). It is not really nessecary unless you host a domain and run email (so that people can email you at [email]you@your.domain.com[/email]).

---

### Post by abyssius on 2009-02-22
> **rhcm123 said:**
> No, postfix is a mail server. When you send emails via thunderbird and evolution, they logon to the remote servers (i'll use gmail as an example) and start an SMTP connection that downloads the mail from smtp.google.com to your local machine. Not to postfix.

Postfix is the actual server that your computer would connect to (it's one of them and the most common, but there are other MTA's). It is not really nessecary unless you host a domain and run email (so that people can email you at [email]you@your.domain.com[/email]).

Thanks again. I got you. I am of course using remote servers for my email accounts. I don't know why ubuntu would set up a mail server on a client desktop. Anyway, postfix is history. Thanks for the education.

---

### Post by rhcm123 on 2009-02-22
> **abyssius said:**
> Thanks again. I got you. I am of course using remote servers for my email accounts. I don't know why ubuntu would set up a mail server on a client desktop. Anyway, postfix is history. Thanks for the education.

No probs. Probably got send by accident with one of the updates

---

### Post by abyssius on 2009-02-22
> **rhcm123 said:**
> No, postfix is a mail server. When you send emails via thunderbird and evolution, they logon to the remote servers (i'll use gmail as an example) and start an SMTP connection that downloads the mail from smtp.google.com to your local machine. Not to postfix.

Postfix is the actual server that your computer would connect to (it's one of them and the most common, but there are other MTA's). It is not really nessecary unless you host a domain and run email (so that people can email you at [email]you@your.domain.com[/email]).

I din't uninstall it yet because I got these messages:
```

root@desktop:/etc/postfix# apt-get --purge remove postfix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++6-4.3-dev libmd5-perl debhelper intltool-debian libbeecrypt6
  g++-4.3 m4 po-debconf ncurses-term g++ libmail-sendmail-perl gettext
  librpm4.4 pax dpkg-dev rpm html2text patch alien libsys-hostname-long-perl
  unhide build-essential
The following packages will be REMOVED:
  bsd-mailx* lsb* lsb-core* lsb-cxx* lsb-desktop* lsb-graphics* lsb-languages*
  lsb-multimedia* lsb-printing* mailx* postfix* realplay* rkhunter* tripwire*
0 upgraded, 0 newly installed, 14 to remove and 49 not upgraded.
After this operation, 30.5MB disk space will be freed.

```
It seems that uninstalling postfix may have consequences beyond removing that program. Is this anything I should worry about?

---

### Post by rhcm123 on 2009-02-22
> **abyssius said:**
> I din't uninstall it yet because I got these messages:
```

root@desktop:/etc/postfix# apt-get --purge remove postfix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++6-4.3-dev libmd5-perl debhelper intltool-debian libbeecrypt6
  g++-4.3 m4 po-debconf ncurses-term g++ libmail-sendmail-perl gettext
  librpm4.4 pax dpkg-dev rpm html2text patch alien libsys-hostname-long-perl
  unhide build-essential
The following packages will be REMOVED:
  bsd-mailx* lsb* lsb-core* lsb-cxx* lsb-desktop* lsb-graphics* lsb-languages*
  lsb-multimedia* lsb-printing* mailx* postfix* realplay* rkhunter* tripwire*
0 upgraded, 0 newly installed, 14 to remove and 49 not upgraded.
After this operation, 30.5MB disk space will be freed.

```
It seems that uninstalling postfix may have consequences beyond removing that program. Is this anything I should worry about?

Those are not related to postfix, and i don't know about why the same apt-session is removing them. You aren't getting dependency complaints, so it seems ok.

---

### Post by abyssius on 2009-02-22
> **rhcm123 said:**
> Those are not related to postfix, and i don't know about why the same apt-session is removing them. You aren't getting dependency complaints, so it seems ok.

The only program I recognize is realplay, which I can always re-install, so I'll do it an see what happens :)

---

### Post by rhcm123 on 2009-02-28
> **abyssius said:**
> The only program I recognize is realplay, which I can always re-install, so I'll do it an see what happens :)

Just clearing old threads from my subscriptions and saw this one. Any luck?

---

