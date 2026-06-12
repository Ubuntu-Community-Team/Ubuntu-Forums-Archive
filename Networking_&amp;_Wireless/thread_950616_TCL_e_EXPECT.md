---
title: "TCL e EXPECT"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by gustavolinux on 2008-10-17
Hi folks, could any tcl and expect programmer help me please?

I'm making a tcl script that just executes one command using ssh, without the need of typing a password manually (tcl sends the password).

I did the 'expect' and 'send' part of the script easily. It waits for the ssh response, sends the correct password and fine. But I don't know how to make the command (the one sent by ssh) display its results on the screen. I need help for this, please.

The segment of the script where I don't know what to do is this:

--------------------------------------

package require Expect;

spawn ssh root@172.21.1.99 ls

expect "Password: "

send "123\r"

?????????

--------------------------------------

As I said, when I execute it (test.tcl), what happens is that the results are not displayed..

--------------------------------------

root@linuxbermudas:/home/root# tclsh ./test.tcl
spawn ssh root@172.21.1.99 ls
Password: root@linuxbermudas:/home/root#

--------------------------------------

The directory list should be displayed...  :(

What I need to do to allow 'ls' to display its results?

thanx in advance

---

