---
title: "C++ system commands"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by iBlackdeath on 2009-09-03
[SIZE=2]cout << [/SIZE][SIZE=2][COLOR=#a31515][SIZE=2][COLOR=#a31515]"Enter in the URL"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] << endl;[/SIZE]
[SIZE=2]cin >> URL;[/SIZE]
[SIZE=2]system([/SIZE][SIZE=2][COLOR=#a31515][SIZE=2][COLOR=#a31515]"Ping"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]);[/SIZE]
 
i am trying to get the URL after the ping but im new in C++ and do not know the code to ping URL

---

### Post by Trebaruna on 2009-09-04
```

#include <iostream>
#include <string>
#include <stdlib.h>

int main()
{
    std::cout << "Enter url: ";
    std::string url;
    std::cin >> url;
    url = "ping " + url;
    return system(url.c_str());
}
```
You should probably go to a C++ forum, though. Try cplusplus.com

---

