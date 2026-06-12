---
title: "How do I get  a program onto the Applications Menu"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by Daanii on 2011-03-02
I've got Ubuntu 10.10 installed on my laptop. I downloaded a program called the Arduino IDE rather than get it through sudo apt-get. (That was the only way to get the latest version.) 

Now I can run the program fine, but I have to go into the right folder, click on the right file, and click on "Run." 

Is there some way to instead get the program listed in the Applications menu so I can just pull down that menu and run the program?

Thank you.

---

### Post by Nytram on 2011-03-02
Right-click on the **Applications** menu and choose **Edit Menus**. From there you can select one of the categories and add **New Item**.

---

### Post by beew on 2011-03-02
You can create a desktop launcher or a menu launcher for it. To create a desktop launcher right click and choose "create desktop launcehr", to create a menu launcher go to System > Preference > Main Menu and choose the category for your application on the left panel and then click add new item. In both cases a dialogue box will show up asking for the program name and the command. The command is usually just the path to the bin file (the file you click to run), say, home/username/program-folder/application. If your application has an icon (or you can download it ) you can click the upper right corner box of the create launcher dialogue box to locate it so your launcher would look nice.

---

### Post by Daanii on 2011-03-03
Great, thanks. I've now got the program and its icon nicely in place.

---

