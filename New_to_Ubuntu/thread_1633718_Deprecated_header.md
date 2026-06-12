---
title: "Deprecated header"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by newport_j on 2010-11-29
[COLOR=black][FONT=Verdana]#warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I get this above error when I use a c++ compiler on some c code; the c code compiles perfectly with gcc. I am aware that it is telling me that I am using a deprecated header. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]According to the line number it is the header[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]<complex.h>[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]in the c code. What is the new header to replace complex.h? [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Newport_j[/FONT][/COLOR]

---

### Post by talonmies on 2010-11-29
<complex>

---

### Post by muteXe on 2010-11-29
and you might have to add:
```

using namespace std;

```

at the top (if you havent already).

---

