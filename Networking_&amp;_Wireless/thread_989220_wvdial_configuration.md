---
title: "wvdial configuration"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by annoe_yk on 2008-11-21
hi everyone,
i would like to ask some question regarding **wvdial** configuration, 
my mobile network setting for an internet connection is:

apn: internet
username: *blank* (no username)
password: *blank* (no password)

but in **wvdial** i couldn't establish the connection if i didn't fill the username or password

can somebody please help me?

fyi: if i fill the username and password, it will do be able to connect to the internet but, my mobile network will charge differently, and quite expensive :( [_IDR 125000/month [without username and password]_ v.s. _IDR 5/KB [if i use the incorrect setting for the apn, username and password]_ ]

---

### Post by Rayaz on 2008-11-21
What if you just use "a" for password and "b" for username? Wvdial needs an username and password to connect, it simply won't work without them.
And welcome to the forums!

---

### Post by annoe_yk on 2008-11-21
uhmmm thanks for reply-ing my post,

if i use other than blank for either username nor password then i will be charge IDR 5/KB, if i use blank for username and password i will only be charge IDR 125000/month for unlimited use of bandwith.

---

### Post by Rayaz on 2008-11-21
If you use a dummy entry like "a", it won't be your password. By the way have been assigned a username and password by your ISP?

---

### Post by annoe_yk on 2008-11-22
as i mention before, that it is possible to use any word as username and password, but it will cost me a lot in the end.
so if i must use '' (empty string) as username and password, how do i write a empty string in the wvdial configuration?

is it correct if i write it down as

username = ''
password = ''

---

### Post by Rayaz on 2008-11-22
Why don't you experiment a little? Try out the empty strings and check for charges? Or try out what I wrote?

---

### Post by annoe_yk on 2008-11-23
Well, its because i can only find out total amount of the billing at the end of the period (monthly).
But thanks, i will try that at the end of the month. :)

---

