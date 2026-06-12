---
title: "Back to File Permissions 101"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-26
ubuntu 8.10 Server

Question...

IF I browse to a folder for example /etc/apache2
and then LEFT Clik on any file or folder a "properties" window opens listing the properties of the file or directory in question.

If I go to the bottom of the properties window there is a "Properties" menu choice.

When I click that, another window pops open called Adminstrator Properties.

If I then click the "Permissions" tab, it shows me the owner, group and other permissions for that file or directory.

**My QUESTION is about the [B]OTHERS** section[/B]

Next to the words "File Access" is a drop down, in that drop down are 4 choices....

1). None
2). Read-only
3). Read and write
4). ---
[COLOR="Red"]
**My question is what exactly does the 4th choice "---" do ?**[/COLOR]

thx and have a nice day.

---

### Post by OffAxis on 2009-02-26
(I don't have gnome installed right now so I'm just guessing)

it's probably execute (depends on how the author of that properties page has it interpret the permissions)

you can always check/uncheck that box and then look at the file permissions from the command line.
```

ls -l
```

---

### Post by bodhi.zazen on 2009-02-26
Well most servers do not run a GUI so it helps if you learn the command line, it will help you in the long run. 

If you want a GUI may I suggest you look at the web interfaces such as webmin ?

At any rate, for permissions, you can use "letters" rather then "numbers" to assign permissions

chmod u+rwx foo
chmod g -wx foo
chmod o -rwx foo

Or numbers

chmod 644 foo

See [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by mistypotato on 2009-02-26
wow...that's a LOT of posts bodhi  :p
I took a look at your link, but noobie that I am, didn't see the answer which was probably staring right at me....sorry.


Maybe I didn't make my question clear....so here it is again. ;)



Question...

I have ubuntu server 8.10 with ubuntu-desktop installed.

IF I browse to a folder for example /etc/apache2
and then LEFT Clik on any file or folder a "properties" window opens listing the properties of the file or directory in question.

If I go to the bottom of the properties window there is a "Properties" menu choice.

When I click that, another window pops open called Adminstrator Properties.

If I then click the "Permissions" tab, it shows me the owner, group and other permissions for that file or directory.

My QUESTION is about the OTHERS section

Next to the words "File Access" is a drop down, in that drop down are 4 choices....

1). None
2). Read-only
3). Read and write
4). ---

**[COLOR="Red"]My question is what exactly does the 4th choice "---" do ?[/COLOR]**


thanks!
):P

---

