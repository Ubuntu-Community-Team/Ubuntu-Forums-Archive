---
title: "install tomcat on karmic"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by codemaniac on 2010-04-05
Hi friends can anyone help me in installing tomcat and configure it to run simple servlet programs..
Thanks..

---

### Post by r-senior on 2010-04-05
The repository version is set up for server use, so it runs as a daemon, no debug and no shutdown on port 8005. This is ideal for running applications but restarting the server and debugging are common tasks during development.

If you want it for development, I'd suggest not installing the version from the repository. What I tend to do is make a $HOME/Software directory and unzip the latest Tomcat distribution into it.

[http://tomcat.apache.org/download-60.cgi#6.0.26]("http://tomcat.apache.org/download-60.cgi#6.0.26")

The bin directory inside the apache-tomcat-<version> directory has startup and shutdown scripts, or you can set it up under the control of an IDE by specifying the Tomcat (Catalina) home directory, shutdown port (8005) and admin user/password.

The user/passwords are defined in ./conf/tomcat-users.xml. I think the comment explains what you need. In particular that your admin user must be part of the "manager" group. For example:

```
<tomcat-users>
    <role rolename="manager"/>
    <user password="manager" roles="manager" username="admin"/>
</tomcat-users>

```

EDIT: Pre-requisite for all this is to install a Java Development Kit (JDK). I'd recommend Sun's (still called Sun's Java after the Oracle acquisition), although OpenJDK does work. Repository versions are fine. You may need to:

$ sudo update-java-alternatives -s java-6-sun

---

### Post by codemaniac on 2010-04-06
Thank you friend for your reply..The link you have posted has many download options..
which one should I downnload???Could you please tell the post download steps too!!

[LIST]
[*]  [zip]("http://www.fightrice.com/mirrors/apache/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26.zip")   ([pgp]("http://www.apache.org/dist/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26.zip.asc"),   [md5]("http://www.apache.org/dist/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26.zip.md5"))
[*]  [tar.gz]("http://www.fightrice.com/mirrors/apache/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26.tar.gz")   ([pgp]("http://www.apache.org/dist/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26.tar.gz.asc"),   [md5]("http://www.apache.org/dist/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26.tar.gz.md5"))
[*]  [32-bit Windows zip]("http://www.fightrice.com/mirrors/apache/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26-windows-x86.zip")   ([pgp]("http://www.apache.org/dist/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26-windows-x86.zip.asc"),   [md5]("http://www.apache.org/dist/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26-windows-x86.zip.md5"))
[*]  [64-bit Windows zip]("http://www.fightrice.com/mirrors/apache/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26-windows-x64.zip")   ([pgp]("http://www.apache.org/dist/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26-windows-x64.zip.asc"),   [md5]("http://www.apache.org/dist/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26-windows-x64.zip.md5"))
[*]  [64-bit Itanium Windows zip]("http://www.fightrice.com/mirrors/apache/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26-windows-i64.zip")   ([pgp]("http://www.apache.org/dist/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26-windows-i64.zip.asc"),   [md5]("http://www.apache.org/dist/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26-windows-i64.zip.md5"))
[*]  [32-bit/64-bit Windows Service Installer]("http://www.fightrice.com/mirrors/apache/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26.exe")   ([pgp]("http://www.apache.org/dist/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26.exe.asc"),   [md5]("http://www.apache.org/dist/tomcat/tomcat-6/v6.0.26/bin/apache-tomcat-6.0.26.exe.md5"))
[/LIST]

Thanks again..

---

### Post by r-senior on 2010-04-06
Either the zip or tar.gz will do bud. Download as you normally do, then:

a. Make a Software directory in your home directory
b. Copy the archive into it
c. Extract it, so that you have $HOME/Software/apache-tomcat-x.x (where x.x is whatever the version is, like 6.0.22).
d. Open a terminal, navigate to $HOME/Software/apache-tomcat-x.x/bin
e. Run the startup script by typing ./startup.sh
f. Open a web browser and try the URL [http://localhost:8080](http://localhost:8080)

You should get a Tomcat welcome page. To use the Tomcat Manager link, you'll need to set up the username and password I showed you above. The Tomcat Manager page will ask for those.

Once you are in to the Tomcat Manager, you can try the examples that come with Tomcat, including viewing their source. Or deploy your own WAR files. Or read the extensive documentation. :)

---

### Post by codemaniac on 2010-04-06
thanks again pal for your detailed help...Have almost done....But couldnot set up the username/password thing..Could you please elaborate what should i put in the file
tomcat-users.xml file to get it work....Whenever I click on the "Tomcat Manager" tag on the
[http://localhost:8080/](http://localhost:8080/) link i am asked the username/password..what exactly i need to put there??????

---

### Post by codemaniac on 2010-04-06
My "tomcat-users.xml" file looks like

> <?xml version='1.0' encoding='utf-8'?>
<tomcat-users>
 <role rolename="manager"/>
 <user username="tomcat" password="tomcat" roles="manager"/>
</tomcat-users>

But whenever i try to access the [Tomcat Manager]("http://localhost:8080/manager/html")  and provide the username/pass  
tomcat/tomcat , i cant acess the tomcat manager...What is the issue here????

---

### Post by codemaniac on 2010-04-06
restarted Tomcat using scripts in the bin directory....
now can acess the manager app....thanks for all the help....

---

