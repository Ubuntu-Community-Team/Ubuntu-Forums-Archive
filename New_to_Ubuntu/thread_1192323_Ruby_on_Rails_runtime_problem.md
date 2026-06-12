---
title: "Ruby on Rails runtime problem"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by typon on 2009-06-20
Hello there Ubuntu gurus, i am really desperate for your help...

I followed this: [https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)

tutorial to install Rails on my Jaunty Jackalope system.

It all installed fine, but when i go into my app's folder and do

```
script/server
```, 

i get this:

```
=> Booting WEBrick
=> Rails 2.3.2 application starting on http://0.0.0.0:3000
=> Call with -d to detach
=> Ctrl-C to shutdown server
[2009-06-20 00:08:55] INFO  WEBrick 1.3.1
[2009-06-20 00:08:55] INFO  ruby 1.8.7 (2008-08-11) [i486-linux]

```

which is good.

But, when i click the 

[SIZE="5"][COLOR="Red"]About your application’s environment[/COLOR][/SIZE]

link, i get the message:

[COLOR="Red"]We're sorry, but something went wrong.[/COLOR]

I then checked the development.log, server.log, production.log and test.log file and they are all empty.



Btw, when i create the app by doing

```
rails my_app
```

or 

```
rails my_app -d mysql
```

i get the same result. Nothing works in the app site.

I really can't figure out why this is happening, if anyone can please i'd be really grateful. 

Thanks in advance.

---

### Post by &#1082;&#1086;&#1084;&#1084;&#1091;&#1085;&#1080;&#1089;&#1090;&#1080;&#1095;&#1077;&#1089;&#1082; on 2009-06-28
It sounds as if Ruby isn't connecting to the database. Make sure you have the correct username and password in your database.yml file. This is the cause for many issues with rails.

---

