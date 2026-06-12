---
title: "Issues with htpasswd"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by Xi0N on 2008-06-03
I have a web server running in my 8.04 machine.
There is a plain text file in /var/www/file.log that i usually access by going to this url: [http://myip/file.log](http://myip/file.log)
The point is that i try to protect that page, setting a password, by going to /var/www directory and running this command:

sudo htpasswd -c .htpasswd User

It asks me to input a new password and creates that file, but i still can enter that url without any autenthication.....
¿Am i doing anything wrong?

Thanks

---

### Post by Kebabman on 2008-06-03
Pretty sure this is off topic but just creating a .htpasswd file will not work. You have to use .htaccess to say where the .htpasswd file is. There is a good tutorial here :

[http://www.cs.dal.ca/studentservices/faq/tutorials/web_sites/htaccess.shtml]("http://www.cs.dal.ca/studentservices/faq/tutorials/web_sites/htaccess.shtml")

Hope this helps...

Forgot to mention, the .htpasswd file should be placed in a non public readable location for security.

---

### Post by Xi0N on 2008-06-03
Thanks! :)

---

