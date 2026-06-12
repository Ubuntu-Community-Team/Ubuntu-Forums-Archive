---
title: "Make sun java as default"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by bhargava470 on 2009-06-15
Hi,

I installed java manully by downloading the file from sun's website in /usr/local/ .
I want to make it the default. i tried to use the update-java-alternatives which doesnt show the sun java (obvious!!!) here's the result

sudo update-java-alternatives --list
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-gcj 1042 /usr/lib/jvm/java-gcj

I used export JAVA_HOME option as pointed in this [link]("http://ubuntuforums.org/archive/index.php/t-366104.html"). But in vain. Can some one tell me what should be done.

Thanks.

---

### Post by sandyd on 2009-06-15
> **bhargava470 said:**
> Hi,

I installed java manully by downloading the file from sun's website in /usr/local/ .
I want to make it the default. i tried to use the update-java-alternatives which doesnt show the sun java (obvious!!!) here's the result

sudo update-java-alternatives --list
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-gcj 1042 /usr/lib/jvm/java-gcj

I used export JAVA_HOME option as pointed in this [link]("http://ubuntuforums.org/archive/index.php/t-366104.html"). But in vain. Can some one tell me what should be done.

Thanks.
```

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-source

```

your covered for everything java. (you do not need sun-java6-source or sun-java6-jdk if you aren't developing apps)

java can also be obtained by installing ubuntu-restricted-extras, but please hide the fact of its existence from everybody as it may be illegal in your country.

---

### Post by bhargava470 on 2009-06-16
> **carlee said:**
> ```

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-source

```your covered for everything java. (you do not need sun-java6-source or sun-java6-jdk if you aren't developing apps)

java can also be obtained by installing ubuntu-restricted-extras, but please hide the fact of its existence from everybody as it may be illegal in your country.

I have already installed java jdk manually (not from the repositories) ... what i need to do it just make this the default (not openjdk, which is the current default) ....  

Thanks

---

### Post by ad_267 on 2009-06-16
See the section on choosing the default Java here: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Or just run:
sudo update-alternatives --config java

---

### Post by kpkeerthi on 2009-06-16
> **bhargava470 said:**
> I have already installed java jdk manually (not from the repositories) 
Thanks
If you installed it manually, the update-alternatives command will not help. You need to set the folder where Java is installed to the PATH environment variable in /etc/profile, or ~/.bash_profile or .bashrc.

---

### Post by ad_267 on 2009-06-16
> **kpkeerthi said:**
> If you installed it manually, the update-alternatives command will not help. You need to set the folder where Java is installed to the PATH environment variable in /etc/profile, or ~/.bash_profile or .bashrc.

Whoops, I should really read the original post more carefully. Sorry about that.

---

### Post by bhargava470 on 2009-06-16
> **kpkeerthi said:**
> If you installed it manually, the update-alternatives command will not help. You need to set the folder where Java is installed to the PATH environment variable in /etc/profile, or ~/.bash_profile or .bashrc.

Thanks kpkeerthi.

---

