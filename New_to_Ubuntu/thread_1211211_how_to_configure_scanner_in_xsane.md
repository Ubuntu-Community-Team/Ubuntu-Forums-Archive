---
title: "how to configure scanner in xsane?"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by AlanRick on 2009-07-12
I have a brother wifi scanner and I'm trying to connect it to my ubuntu pc.
I've followed brother's instructions and installed the driver (verified with grep).

In another post I found "> Simply open Xsane, choose you scanner and click OK. "

When I open xsane I get three windows but I can't find a button to set the driver (or search the wifi for the driver like with printers)

Question is - where is the button/menu to select the driver?
Alan

---

### Post by AlanRick on 2009-07-12
The "choice" is only available when you have completed installing the scanning software and there are alternatives to choose from.

Once I'd executed:
```
 brsaneconfig3  -a  name=WifiScanner  model=MFC-7840W  ip=123...
```
in the terminal (as described in the brother online documentation) the choice magically appeared in the xsane preview window (radio buttons).

Hope this is of use to someone else,
Alan

---

