---
title: "xEmacs fonts do not load"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by itsmilesdavis on 2010-08-07
Running Ubuntu 64-bit Lucid.  Running Xming+Putty in WinVista to connect.

Installed xemacs21
```
sudo apt-get install xemacs21
```
If I run xemacs &, the program loads, but there is an error:
```

Warning: Cannot convert string "-*-helvetica-bold-r-*-*-*-120-*-*-*-*-iso8859-*" to type FontStruct
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-helvetica-bold-r-*-*-*-120-*-*-*-*-iso8859-*,                        -*-*-*-*-*-*-*-120-*-iso10646-1,           -*-*-*-*-*-*-*-120-*-jisx0208.1983-0,                    -*-*-*-*-*-*-*-120-*-jisx0201.1976-0" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Missing charsets in String to FontSet conversion

```

I googled around, but could not find a solution which worked.  If I'm in xemacs, I can't change the fontsize or anything.  It's really frustrating.

[HTML]http://fedoraforum.org/forum/showthread.php?t=223428[/HTML]

They mention installing fonts.  So, I installed some of the xfonts with apt-get (most I ran were already installed.

One thing worth noting is that ~/.xemacs/ does not even exist. I thought this was automatically generated.  Where is xemacs getting the configuration information from?  

I have already uninstalled and reinstalled xemacs.

Any help is greatly appreciated.

---

### Post by itsmilesdavis on 2010-08-07
Now that I think of it, this probably does not belong in "Absolute Beginner Talk".

---

