---
title: "Importing address list into Evolution"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by mynot on 2009-05-07
Hello.
I have a file called, at present, maillist.csv. It contains entries like the following:
John Smith, <john.smith@somemialaddress>
Mary Jones, <mary.jones@anotheremailaddress>
etc.
It does not come from any other email program. It's just a file created with a text editor.
I want to import it into Evolution so that I get entries in the Full Name and Email columns. 
It cannot be difficult, but 2 hours and I've got nowhere (apart from importing T/bird, which I don't want).
Thanks
Tony

---

### Post by scheuri on 2009-05-07
Hi there

I never imported anything else than a exported address list (which format I just can not think of right at the moment, ldif?), so I never had that problem.

However, you will surely run in any case into problems because the names (first name and last name) seem (according to your post) be in the same line without a separator such as comma or point.
You separate your names and your mailaddresses with a comma, but not the names itself.
It might not solve the problem itself, however if you change that you might have better chances to import those information.

As I have not evolution available to test, I can not guide you or make suggestions.
Maybe you post all the file extensions that evolutions offers you to import....

good luck
cheers
scheuri

---

### Post by mynot on 2009-05-07
Scheuri,
Thanks, but I've tried that, also tab separator. At best it imports everything into the Full Names column.
Tony

---

### Post by ikke2808 on 2009-05-12
Hey mynot,

Just been playing with importing excel addresses into evolution 2.22.

Make a csv where lines look like this :
First_Name,Last_Name,Screen_Name,Nickname,Email_Address,Email_2_Address,Business_Phone,Home_Phone,Business_Fax,Pager,Mobile_Phone,Home_Street,Home_Street_2,Home_City,Home_State,Home_Postal_Code,Home_Country,Business_Street ,Business_Street_2,Business_City,Business_State,Business_Postal_Code,Business_Country,Title,Department,Organization,Business_Web,Web_Page,Screen_Name,Title,u,v,w,x,y,Notes ,z

Nou you can import using the Mozilla csv definition. Worked fine for me.

Cheers,

Frank.

---

