---
title: "Add/Remove"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by Howie Williams on 2009-10-20
When I click on add/remove I get this error message.

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

HELP!!!!!!

---

### Post by HarrisonNapper on 2009-10-20
Have you tried the following steps yet?

> 1. Check for broken packages with synaptic
2. Check the file permissions and correctness of the file '/etc/apt/sources.list'
3. Reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'

---

### Post by tarps87 on 2009-10-20
Run
```
sudo apt-get update && sudo apt-get install -f
```
Note: you will need to be connected to the internet

---

