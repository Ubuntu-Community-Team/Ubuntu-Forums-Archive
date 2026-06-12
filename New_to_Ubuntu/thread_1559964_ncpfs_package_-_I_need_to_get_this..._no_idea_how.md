---
title: "ncpfs package - I need to get this... no idea how"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by beanco on 2010-08-24
Trying to log onto our Novel Network here at the HS. 

All I could figure out so far was this,, instructions given to a colleague on our IT tech page  ... There are no real steps just this code:


```
ncpfs package:
ncpmount -o tcp -A 10.0.0.3 -S polinetware -U <júzernév> -y iso8859-2 -p cp852 -s <könyvtárnév>
```

OK, juzernev = username - no problem for me there.

konyvtar = library/directory - suppose that means I need to make a directory for this... say novel  

but, what the hell do I do to get/install/mount whatever all this stuff....

Our IT guru is not round, the others in the IT dept, know nothing about linux and just send me away as they are busy and I am the only one using linux.

So, please take me through, step by step.

I am on Karmic... I would like to access the Novel Network and if I get it done with your help, I will dazzle our guru and have fun learning sg new.

thanks

robi

---

### Post by earthpigg on 2010-08-24
You've tried this, right? Can you be more detailed about the problem you are having, please.

see attached...

---

### Post by Calash on 2010-08-24
Library may mean your tree or Novell Context.

The Tree will point to the root of your Novell Tree.  Context will be something like users.div.na.corp and point to the location of your account in the tree.

Unfortunately if you do not know the information you may have to wait for your IT people as it will be specific to your network.  You may be able to get the information from a Windows computer by looking at the Novell client.

For the install see the previous post.

---

### Post by beanco on 2010-08-24
OK, I have this ubuntu laptop.

The entire school uses Windows. And a Novel network. Currently, I cannot access the Novel Network from this Ubuntu set up.

That is what I want to set up, I want to get access to the Novel Network.

I dug round our IT FAQ and found a post form which I quoted above.

Earthpig, I tried your suggest to no avail. What bout CL?

Robi

---

### Post by earthpigg on 2010-08-24
i've never tried to connect to a novell network, so im not sure.

have you read the manual for ncpmount and ncpfs?
```

man ncpmount
man ncpfs
```

---

### Post by beanco on 2010-08-25
I froget about that on a regular basis... thanks for the tips...

I tried, to no avail

```
rob@rob-laptop:~$ man ncpmount
No manual entry for ncpmount
rob@rob-laptop:~$ man ncpfs
No manual entry for ncpfs
```

---

