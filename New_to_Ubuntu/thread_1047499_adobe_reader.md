---
title: "adobe reader"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by ericgds on 2009-01-22
I installed the adobe plug in yesterday with some help form someone telling me the correct version to find and install.  I now need to install adobe reader, can someone tell me the right way to so so?

---

### Post by taurus on 2009-01-22
The easy way is here, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

---

### Post by ericgds on 2009-01-22
> **taurus said:**
> The easy way is here, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

It says go to applications add remove and search for adobe or reader then install but no adobe reader shows up.  Nothing adobe shows up.

---

### Post by Nepherte on 2009-01-22
And did you add the medibuntu repository?

---

### Post by taurus on 2009-01-22
Did you add Medibuntu's repo to your /etc/apt/sources.list.d first?

---

### Post by ericgds on 2009-01-22
> **Nepherte said:**
> And did you add the medibuntu repository?

The what?  No. I don't know what that is.

---

### Post by taurus on 2009-01-22
Please read the link in my post #2.  It shows you exactly how to add it to your /etc/apt/sources.list.d/.

---

### Post by ericgds on 2009-01-22
> **taurus said:**
> Did you add Medibuntu's repo to your /etc/apt/sources.list.d first?

No.

---

### Post by ericgds on 2009-01-22
Oh.  Ok.  Am I doing something illegal?  I don't like that idea.  Why does it say seek legal adivice if you aren't sure about certain laws in your country.  Im in america.

---

### Post by ericgds on 2009-01-22
> **taurus said:**
> Please read the link in my post #2.  It shows you exactly how to add it to your /etc/apt/sources.list.d/.

OK, I'm using 8.10.  So do I just cut and paste the info into my terminal?

---

### Post by taurus on 2009-01-22
Yes, cut 'n paste is the easiest way.

```

sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install acroread
```

---

