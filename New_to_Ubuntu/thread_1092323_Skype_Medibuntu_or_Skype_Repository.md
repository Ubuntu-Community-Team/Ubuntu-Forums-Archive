---
title: "Skype: Medibuntu or Skype Repository?"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by js@lloyd on 2009-03-10
I'd like to install Skype today.  I've looked a Medibuntu, and tried to install it yesterday, but don't think i was succussful. Being new, I'm sure I didn't follow the instructions correctly. I referenced this link, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and typed the following into a terminal then exited. 

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)

Do I need use both lines? 

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Thanks the help.

---

### Post by taurus on 2009-03-10
Just run the second one.  Then, install the GPG key and off you go.

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by treesurf on 2009-03-10
You can check to see if you have medibuntu in your sources list by going to System>Administration>Software Sources and clicking on the Third Party Software tab.  There should be a line for packages.medibuntu.org/intrepid in there.  If you find it isn't there go to terminal and cut and paste this command (assuming you are using intrepid):

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Then you need to get the gpg key so cut and paste:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Click yes if it asks you for approval.

Then you can install Skype from Medibuntu!

EDIT:  I'm too slow!

---

