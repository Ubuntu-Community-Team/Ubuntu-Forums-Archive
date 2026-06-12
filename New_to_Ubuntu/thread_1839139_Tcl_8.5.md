---
title: "Tcl 8.5"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by nogi on 2011-09-05
I am running 11.04 and am having problems running a tcl script:
 
```
 
can't find package dict
    while executing
"package require dict"
    invoked from within
"if {$::tcl_version < 8.5} {
    package require dict
}"
    (file "/usr/share/tcltk/tcllib1.12/json/json.tcl" line 11)
    invoked from within
"source /usr/share/tcltk/tcllib1.12/json/json.tcl"
    ("package ifneeded" script)
    invoked from within
"package require json"
    (file "./lcd_sabnzbd.tcl" line 113)

```[FONT=Courier New][/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]I'm told that I need to have tcl 8.5 installed. How do I check this and if I have the wrong version, how to I go about upgrading? Otherwise, how do I install dict?[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]I have already tried this with no luck:[/FONT]
[FONT=Courier New][/FONT] 
```
 
sudo apt-get install tcllib
sudo apt-get install dict


```

---

### Post by squaregoldfish on 2011-09-05
The dict command was added in Tcl 8.5. You can install the tcl8.5 package to get it.

If that's not an option for some reason, there's a package that provides the dict command from Tcl 8.4. You can get it from here:

[http://www.flightlab.com/~joe/gutter/packages/dict.html](http://www.flightlab.com/~joe/gutter/packages/dict.html)

Steve.

---

### Post by nogi on 2011-09-05
Ok, this fixed the TCL issue I think:
```
sudo apt-get remove tk8.4 tcl8.4
sudo apt-get install tk8.5 tcl8.5
```But now I am getting this:
```
can't find package tls
    while executing
"package require tls"
    (file "./lcd_sabnzbd.tcl" line 114)
```What package is tls in?

---

### Post by squaregoldfish on 2011-09-05
I don't know. It will probably be available in Ubuntu's repositories, or you'll be able to download it from elsewhere on the net.

Search Synaptic first!

Steve.

---

### Post by gmargo on 2011-09-05
Probably the **tcl-tls** package.

```

$ apt-cache search tcl | grep tls
tcl-tls - the TLS OpenSSL extension to Tcl

```

---

