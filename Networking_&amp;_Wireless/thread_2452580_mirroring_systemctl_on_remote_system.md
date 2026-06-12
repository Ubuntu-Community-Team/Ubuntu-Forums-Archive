---
title: "mirroring systemctl on remote system"
date: 2020-10-24
forum: Networking &amp; Wireless
---

### Post by tjcstuart on 2020-10-24
[COLOR=#22231F][FONT=&quot]I can run systemctl --host username@192.168.1.42 status servicename then enter the password and I get the status of servicename on a remote host, I can also stop/start/etc....Would it be possible to build a local service that is basically just that "remote" command? In essance creating a local mirror of a service on a remote machine? It would have to include the password too, which this being an internal network isn't an issue for security.[/FONT][/COLOR]

---

### Post by scorp123 on 2020-10-25
> **tjcstuart said:**
> [COLOR=#22231F][FONT=&quot]I can run systemctl --host username@192.168.1.42 status servicename then enter the password and I get the status of servicename on a remote host, I can also stop/start/etc....Would it be possible to build a local service that is basically just that "remote" command? In essance creating a local mirror of a service on a remote machine? It would have to include the password too, which this being an internal network isn't an issue for security.[/FONT][/COLOR]

You might want to look into **Ansible**...
[https://www.ansible.com/community]("https://www.ansible.com/community")

With Ansible you can define so called "playbooks" that say e.g. you want a certain service on a certain port running. You also define a hosts inventory file where you can group your servers by function, location, OS, distribution ... or all of those criteria.

You'd then execute that playbook and apply it on all your servers e.g. in Europe. And Ansible will reply with "OK" messages when it didn't need to do anything (the server was already configured the way you want), "changed" when it actually needed to do something (e.g. activate the service), or "failed" if it wasn't able to connect to the server you wanted (e.g. because it's down for maintenance).

The point being that you get what you wanted: Multiple servers are then configured exactly the same way and are doing exactly the same thing and are running exactly the same services. Or not running them.... depending on what your Playbook is telling them to do or not.

So there's no need to "reinvent the wheel". Ansible already offers these possibilities and if you are in charge of multiple servers (e.g. because of your job?) you should definitely investigate further and consider learning it.


EDIT: Link corrected.

---

