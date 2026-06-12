---
title: "problem with system command"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by shivaprakashreddy on 2011-05-11
[SIZE=4][B] i am executing su=system(smbmount //......) 
after  failure of mounting su=-1 and even  after successful mounting value of su is -1.
wt is the problem? 
can any one help me out??????????[/B][/SIZE]

---

### Post by r-senior on 2011-05-11
Is this in a C program? Could you post a more complete example of the code?

Please remember to use code tags around it so it formats correctly - there are buttons on the post page that help you do this. Near the ones that you used to make your font bold.

---

### Post by shivaprakashreddy on 2011-05-12
[SIZE=2] printf("enter host ip\n");
   scanf("%s",ipadd);
   printf("enter share name\n");
   scanf("%s",share);
   sprintf(mntcomm,"smbmount //%s/%s /media/%c -o -r",ipadd,share,letter);
   su=system(mntcomm);
   printf("su=%d\n",su);

   Here  the value of su is -1 after succesful mounting and after failure of mounting.[/SIZE]

---

