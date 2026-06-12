---
title: "Cant tunnel webmin through ssh properly"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by cK` on 2010-04-07
Hello everyone,

I am trying to tunnel webmin through ssh on my unbuntu server ( I want to only have the ssh port open and still be able to use webmin).

I am trying to do this with putty while following this tutorial

[http://support.suso.com/supki/SSH_Tutorial_for_Windows](http://support.suso.com/supki/SSH_Tutorial_for_Windows)

I am using putty with a windows machine. 

 Towards the bottom of the tutorial it shows me how to tunnel programs.

Now this is what i am doing.
[IMG]http://i447.photobucket.com/albums/qq199/cking111/Untitled-2.jpg[/IMG]




for my source port i put 10000.

then i put user.dyndns.com:10000 for the destination.

i click add then  then i go to session and save. then proceed to login to ssh

but i still cannot log get to user.dyndns.com:10000 through my web browser on my windows machine.

Am i doing somthing wrong?

---

### Post by OriginalName on 2010-04-07
> **cK` said:**
> Hello everyone,

but i still cannot log get to user.dyndns.org:10000 through my web browser on my windows machine.



Hi, I think you'd need to put localhost:10000 in the web browser not the remote address...  :)

---

### Post by cK` on 2010-04-07
> **OriginalName said:**
> Hi, I think you'd need to put localhost:10000 in the web browser not the remote address...  :)

Yes,

The destination points towards what i want to open.
In this case i want to open webmin in my web browser with port 10000 closed( i want to have port 10000 closed on my router and access it through port 22).

At least thats what i think i want to do:(

---

### Post by cK` on 2010-04-07
Well i this is my conclusion.

I cannot do it because my computer is on the same network that the server is on.

Therefore if i close port 10000 the server no longer has access to webmin.

Its amazing how long that took me.

---

