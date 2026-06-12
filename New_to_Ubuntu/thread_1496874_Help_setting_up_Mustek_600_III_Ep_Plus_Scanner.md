---
title: "Help setting up Mustek 600 III Ep Plus Scanner"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by danny3d on 2010-05-29
I followed the steps in the help section of Ubuntu 10.04 but the scanner is not detected. So far I installed the libsane-extras package.and edited out the # from the driver but the scanner is not detected in Xsane.The scanner is listed as one that works in the SANE site. I am totally new to Linux but I am determined to learn. The scanner has a parallel port connection to my computer. I would greatly appreciate some help.

---

### Post by kingcharles1666 on 2011-01-08
In order to get this to work install the package: xsane
You can install using synaptic or manual whatever you prefer.

Next we need to enable the correct drivers:

For Ubuntu 10.04 open a terminal:

```
sudo gedit /etc/sane.d/dll.conf
```
In the editor
Remove the: # (uncomment) which is before the word:
mustek_pp
Save and close the file

Then in the terminal again:

```
sudo gedit /etc/sane.d/mustek_pp.conf
```
In the editor look for the section:
# auto probing:

And remove the: # (uncomment) which is before the line:
scanner mustek-ccd300 * ccd300

Save and close the file and if you are lucky it should work.
If it still does not work you need to run the program as root.
in the terminal type:

```
sudo xsane
```

If it works you can choose to work like this or fix the permissions problem by reading further [here]("http://ubuntuforums.org/showthread.php?t=783599")

---

