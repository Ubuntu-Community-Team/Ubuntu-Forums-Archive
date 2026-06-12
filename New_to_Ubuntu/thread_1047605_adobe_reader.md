---
title: "adobe reader"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by ericgds on 2009-01-22
I have installed the repository.  Can someone tell me how to install adobe reader.

---

### Post by stchman on 2009-01-22
> **ericgds said:**
> I have installed the repository.  Can someone tell me how to install adobe reader.

I am assuming you mean Adobe Acrobat reader.

It is available in the Medibuntu repositories.

I am going to assume you installed Intrepid on your system.  DO the following in a terminal:

```

sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install acroread

```

For reading PDFs Evince does a decent job so Acrobat reader is not really needed.

---

### Post by taurus on 2009-01-22
Serious, do you even read the replies to your original thread before you created a new one of the same topic?

[http://ubuntuforums.org/showthread.php?t=1047499](http://ubuntuforums.org/showthread.php?t=1047499)

---

### Post by ericgds on 2009-01-22
> **taurus said:**
> Serious, do you even read the replies to your original thread before you created a new one of the same topic?

[http://ubuntuforums.org/showthread.php?t=1047499](http://ubuntuforums.org/showthread.php?t=1047499)

Yes.  you told me to install the repositoty, which I think I did.  Now what do I do.

---

### Post by stchman on 2009-01-22
I am aware of n00bies to Linux, but when someone gives clear precise instructions it is hard not to get irritated.

---

### Post by ericgds on 2009-01-22
> **stchman said:**
> I am aware of n00bies to Linux, but when someone gives clear precise instructions it is hard not to get irritated.

Your instructions are clear.  I will do what you said.

---

### Post by stchman on 2009-01-22
> **ericgds said:**
> Yes.  you told me to install the repositoty, which I think I did.  Now what do I do.

Ok, I will give you the absolute easiest simple instructions I can.

Open a terminal(I am going to assume you can do that).

Type this in:
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list

```

Then do this in the terminal when the first item is completed.
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Then install Adobe acrobat 8 by typing in the terminal again
```
sudo apt-get install acroread
```

Acrobat 8 will be installed after all is finished.

---

### Post by FrankVdb on 2009-02-02
And then everything went silent. 

He probably fell off his chair when reading your instructions. :D

---

### Post by stalkingwolf on 2009-02-02
Why are you installing adobe reader?  There is a native pdf reader installed.  at least I dont recall installing it, unless it was included in something like restricted extras.  yet I can read all pdf files I have.

:-k

---

### Post by taurus on 2009-02-02
> **stalkingwolf said:**
> Why are you installing adobe reader?  There is a native pdf reader installed.  at least I dont recall installing it, unless it was included in something like restricted extras.  yet I can read all pdf files I have.

:-k

Evince.

---

