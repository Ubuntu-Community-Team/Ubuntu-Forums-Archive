---
title: "stream.h and fstream.h NOT FOUND"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by balachandarlinks on 2009-06-06
Hai,
  I recently installed Ubuntu 8.10.Actually I need g++ for my project.So I installed it through synaptic.I installed g++,g++ 4.1,g++4.2,g++ 4.3 all shown in synaptic.
  But when i compile my project it says,
        stream.h - No Such File or Directory Found
        fstream.h - No Such File or Directory Found

  I m really in need of these headers.Pls help me to get rid of it soon.Thank you....
                              cheers.....

---

### Post by ibuclaw on 2009-06-06
It's available in the package:
```
libstdc++6-4.2-dev
```
Which only requires g++-4.2, so you can remove g++-4.1, as it is not needed.

Although, you may want to review/update your code in the near future, as those headers appear to have been removed/deprecated in the g++-4.3 lib/headers.

By having a quick look at just what is in those headers, all that needs doing is replace "#include <stream.h>" with
```
#include <iostream>
```
and "#include <fstream.h>" with
```
#include <fstream>
```

Regards
Iain

---

### Post by balachandarlinks on 2009-06-06
Thank you tinivole...I ll try it soon and reply you...;-)

---

### Post by sirene on 2009-06-15
sorry.

---

### Post by mrchrismnh on 2010-01-08
I tried installing those libraries and <fstream.h> is still not recognized. I can use <fstream> fine though but I had to take out all my instances of std::fstream foo; and stick a using namespace std; at the top of the file, which I despise. Is this normal? I am using Karmic Koala.

---

