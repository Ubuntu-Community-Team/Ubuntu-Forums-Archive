---
title: "Missing the close &quot;x&quot; and minimize &quot;_&quot; buttons after upgrade."
date: 2009-11-01
forum: New to Ubuntu
---

### Post by dhoupt on 2009-11-01
The close box and minimize button are gone from the top right corner of each open window???      

The only minor annoyance after upgrade to KK, otherwise it is beautiful.

    Thanks to all who help develop test and fix!!!

---

### Post by ovroniil on 2009-11-01
I am a noob but I think it can be curable.

To fix the problem press **CTRL+F2**. Then write **gconf-editor** and click on **Run**. Now go to **apps--> metecity --> general**. From the right side menu find out the **button_layout** and click it**.  **As you said you dont have 'close' and 'minimize' button it should show that "menu:maximize". To show all buttons just write "**menu:minimize,maximize,close,**". 

Think it will help you.

---

### Post by Darce on 2009-11-01
Do you have compiz installed ?

If so, go to System->Preferences->Compiz Settings Manager

       Scroll down to Effects and place a tick next to Windows Decoration.

Ran into this problem a few months ago.

Hope it helps   :)

Cheers,

Tim

---

### Post by dhoupt on 2009-11-01
"Go to System->Preferences->Compiz Settings Manager
       Scroll down to Effects and place a tick next to Windows Decoration."

"To fix the problem press **CTRL+F2**. Then write **gconf-editor** and click on **Run**. Now go to **apps--> metecity --> general**. From the right side menu find out the **button_layout** and click it**.  **As you said you dont have 'close' and 'minimize' button it should show that "menu:maximize". To show all buttons just write "**menu:minimize,maximize,close,**". "

Thanks Darce & ovroniil for your replies!

   BUT, tried the above sugestions: Win. Dec. is checked / **menu:minimize,maximize,close **is already there[B] ?????

[/B]Any other ideas?

---

