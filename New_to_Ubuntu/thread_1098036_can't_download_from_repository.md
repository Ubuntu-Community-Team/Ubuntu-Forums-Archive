---
title: "can't download from repository"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by hosmer on 2009-03-16
I tried going to the medibuntu repository.
Now when I start synaptic package manager I get the following message.

E: Type'--2009-03-16' is not known on line1 in source list/etc/apt/
sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E:_cache->open() failed, please report

I'd like to get back to the ubuntu repository but have no idea how to do it.:confused:

---

### Post by kanikilu on 2009-03-16
Sounds like something just got uncommented or whatever. Can you post the contents of the following file?

/etc/apt/sources.list.d/medibuntu.list

---

### Post by Botbob89 on 2009-03-16
This happened with me on more than one occasion recently...

As Kanikilu said, something's probably been uncommented, your best bet is to find the line with that phrase in and see if it has a # in front of it, and if it hasn't add one.

That is what was wrong in ALL my problems, so try that.

---

### Post by taurus on 2009-03-16
Here's a link to Medibuntu.  Just reinstall the repo.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by hosmer on 2009-03-16
is this the complete code i should enter?
when i entered it all i got was Permission denied

---

### Post by kanikilu on 2009-03-16
> **hosmer said:**
> is this the complete code i should enter?
when i entered it all i got was Permission denied I'm not sure if you meant to copy and paste something there, but, try this.

- Open a terminal: Applications > Accessories > Terminal
- Type ```
cat /etc/apt/sources.list.d/medibuntu.list
``` and press enter
- Highlight the output in the terminal and go to Edit > Copy and then paste it into a reply here.

---

### Post by hosmer on 2009-03-16
> **Botbob89 said:**
> This happened with me on more than one occasion recently...

As Kanikilu said, something's probably been uncommented, your best bet is to find the line with that phrase in and see if it has a # in front of it, and if it hasn't add one.

That is what was wrong in ALL my problems, so try that.

My basic problem is that i'm so new to Lenux that i have to be led in babby steps. I'd be happy to just get back to before i screwed this up.

---

### Post by hosmer on 2009-03-16
user1@user1-desktop:~$ cat /etc/apt/sources.list.d/medibuntu.list
--2009-03-16 15:05:56--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 230 [text/plain]
Saving to: `intrepid.list'

     0K                                                       100% 4.51M=0s

2009-03-16 15:05:57 (4.51 MB/s) - `intrepid.list' saved [230/230]

user1@user1-desktop:~$

---

### Post by drs305 on 2009-03-16
Just reinstall the medibuntu list:
For Intrepid - for other versions replace "intrepid" with the version you are using.
The codes are from the link taurus gave you:
```

sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

---

### Post by hosmer on 2009-03-16
> **drs305 said:**
> Just reinstall the medibuntu list:
For Intrepid - for other versions replace "intrepid" with the version you are using.
The codes are from the link taurus gave you:
```

sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Looks like that did it.
Thanks to all for the help!

Hosmer Grunch

---

