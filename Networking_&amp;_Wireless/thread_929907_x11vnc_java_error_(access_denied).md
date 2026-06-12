---
title: "x11vnc java error (access denied)"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by jvincent08 on 2008-09-25
I'm using x11vnc and vnc-java. The command I use to start the server is: ```
x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800
```
Now, when I try to connect to *my_ip*:5800, the Java applet loads fine, but when I enter my password, I get: ```
java.security.AccessControlException: access denied (java.net.SocketPermission *my_ip*:5900 connect,resolve)
```
Google reported something about signed applets, but wasn't much help. Any ideas? Thanks in advance.

---

### Post by krunge on 2008-09-26
> **jvincent08 said:**
> ```
java.security.AccessControlException: access denied (java.net.SocketPermission *my_ip*:5900 connect,resolve)
```


If your web browser is using a web-proxy server to reach the internet that would cause a java applet problem:

[http://www.karlrunge.com/x11vnc/index.html#faq-ssl-java-viewer-proxy]("http://www.karlrunge.com/x11vnc/faq.html#faq-ssl-java-viewer-proxy")

Although it sounds more like like this ~/.java.policy setting could be the problem:

[http://readlist.com/lists/lists.sourceforge.net/vnc-tight-list/0/938.html]("http://readlist.com/lists/lists.sourceforge.net/vnc-tight-list/0/938.html")

I have never see this problem before. Post your Java Run Time's default java.policy file here.

---

### Post by jvincent08 on 2008-09-26
Thanks for your reply.
> **krunge said:**
> If your web browser is using a web-proxy server to reach the internet that would cause a java applet problem:

[http://www.karlrunge.com/x11vnc/index.html#faq-ssl-java-viewer-proxy]("http://www.karlrunge.com/x11vnc/index.html#faq-ssl-java-viewer-proxy")

I'm not using a web-proxy, but I'm using a school laptop and their network probably has a proxy of some sort set up.
> Although it sounds more like like this ~/.java.policy setting could be the problem:

[http://readlist.com/lists/lists.sourceforge.net/vnc-tight-list/0/938.html]("http://readlist.com/lists/lists.sourceforge.net/vnc-tight-list/0/938.html")

I have never see this problem before. Post your Java Run Time's default java.policy file here.

I do not have a ~./.java.policy file. However, there is what appears to be a system-wide java.policy file in /etc/java-6-sun/security. Here it is:
```

// Standard extensions get all permissions by default

grant codeBase "file:${{java.ext.dirs}}/*" {
        permission java.security.AllPermission;
};

grant codeBase "file:/usr/lib/jvm/java-6-sun-1.6.0.06/ext/*" {
        permission java.security.AllPermission;
};

// Comment this out if you want to give all permissions to the
// Debian Java repository too:
//grant codeBase "file:/usr/share/java/repository/-" {
//        permission java.security.AllPermission;
//};


// default permissions granted to all domains

grant { 
        // Allows any thread to stop itself using the java.lang.Thread.stop()
        // method that takes no argument.
        // Note that this permission is granted by default only to remain
        // backwards compatible.
        // It is strongly recommended that you either remove this permission
        // from this policy file or further restrict it to code sources
        // that you specify, because Thread.stop() is potentially unsafe.
        // See "http://java.sun.com/notes" for more information.
        permission java.lang.RuntimePermission "stopThread";

        // allows anyone to listen on un-privileged ports
        permission java.net.SocketPermission "localhost:1024-", "listen";

        // "standard" properies that can be read by anyone

        permission java.util.PropertyPermission "java.version", "read";
        permission java.util.PropertyPermission "java.vendor", "read";
        permission java.util.PropertyPermission "java.vendor.url", "read";
        permission java.util.PropertyPermission "java.class.version", "read";
        permission java.util.PropertyPermission "os.name", "read";
        permission java.util.PropertyPermission "os.version", "read";
        permission java.util.PropertyPermission "os.arch", "read";
        permission java.util.PropertyPermission "file.separator", "read";
        permission java.util.PropertyPermission "path.separator", "read";
        permission java.util.PropertyPermission "line.separator", "read";

        permission java.util.PropertyPermission "java.specification.version", "read";
        permission java.util.PropertyPermission "java.specification.vendor", "read";
        permission java.util.PropertyPermission "java.specification.name", "read";

        permission java.util.PropertyPermission "java.vm.specification.version", "read";
        permission java.util.PropertyPermission "java.vm.specification.vendor", "read";
        permission java.util.PropertyPermission "java.vm.specification.name", "read";
        permission java.util.PropertyPermission "java.vm.version", "read";
        permission java.util.PropertyPermission "java.vm.vendor", "read";
        permission java.util.PropertyPermission "java.vm.name", "read";
};
```

---

