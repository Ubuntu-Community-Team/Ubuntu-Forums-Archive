---
title: "[SOLVED] Repositories are bad 8.10"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by myolbug on 2008-12-08
I cannot get updates because I am getting connection refused for all repositories.  How do I find out what are the right ones to use?

---

### Post by lovelyvik293 on 2008-12-08
Are you using any type of proxy in your network?

---

### Post by Anicka on 2008-12-08
You need to be a bit more specific in your post in order to get a good answer, so here are some things you should tell us.

Which server are you trying to connect to?

Is it the first time that you are trying to update? In that case it could be something with your network connection, so next question: Can you connect to any webpage at all?

If you have updated via apt/synaptic/aptitude/update-manager before (with success): have you changed something with your network-connection? If not, it can just be that the server you are trying to connect to is temporarily down and will be back in five minutes.

---

### Post by myolbug on 2008-12-08
I realized what it was, and yes it was because of a proxy.  A short while ago, I installed anon-proxy from the synaptic package manager.  I uninstalled it and restarted the machine, (it didn't take until I restarted.) and all is well now.

Thanks for the advice to both of you.

Randy

---

### Post by lovelyvik293 on 2008-12-08
Welcome for the thanks and always mention the details as Anicka said.

---

### Post by meindian523 on 2008-12-08
Please mark the thread solved.

---

### Post by Anicka on 2008-12-08
Good that you found the reason of you problem. So, once again the universal "fix of almost any problem" worked.

---

