---
title: "C++ Help"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by Anthony_25802580 on 2010-10-06
I am working on a project where it asks the user to type in there full name. i cant remember how to get there full name into a string. i have been trying getline but its not working. if you could help it would be much appreciated! Thanks!

---

### Post by GlazedDonut on 2010-10-06
string name;
cin>>name;

---

### Post by Locke_99GS on 2010-10-07
```

#include <string>
using std::string;

```

and use the *string* datatype

or

declare the string as an array of characters.

```

char myName[25]='Locke';

```

and treat it as such. (cin>> will stop reading at whitespace. Try cin.getline or cin.get)

---

