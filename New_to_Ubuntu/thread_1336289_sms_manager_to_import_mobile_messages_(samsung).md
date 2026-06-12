---
title: "sms manager to import mobile messages (samsung)?"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by medya on 2009-11-24
Does anyone know a software that can import my mobile's text mesages (sms) ?
I want to save my text messages on my ubuntu PC  .

---

### Post by llamabr on 2009-11-24
```
brock@hops:~$ apt-cache search sms mobile
gammu - mobile phone management utility
gammu-smsd - SMS message daemon
gnokii-smsd - SMS Daemon for mobile phones
gnokii-smsd-mysql - SMSD plugin for MySQL storage backend
gnokii-smsd-pgsql - SMSD plugin for PostgreSQL storage backend
gnome-phone-manager - control aspects of your mobile phone from your GNOME 2 desktop
gsm-utils - GSM mobile phone access applications
libgammu-dbg - mobile phone management library (debugger symbols)
libgammu-dev - mobile phone management library (development files)
libgammu-i18n - mobile phone management library (i18n files)
libgammu6 - mobile phone management library
libgsmme1c2a - GSM mobile phone access library
libgsmsd6 - SMS daemon helper library
libnet-smpp-perl - Net::SMPP is an implementation of Short Message Peer to Peer protocol over TCP
scmxx - Exchange data with Siemens mobile phones
sms-pl - Send SMs via Polish GSM operators
smsclient - A program for sending short messages (SM / SMS)
wammu - GTK application to control your mobile phone
skysentials - extra functionalities for Linux Skype client
brock@hops:~$ 

```

---

### Post by Steve.G on 2009-11-24
If it's a CDMA phone you can use Bitpim to backup SMS messages. It's in the repository, though the latest test build has support more support for new phones. You can get it at Bitpim.org

---

