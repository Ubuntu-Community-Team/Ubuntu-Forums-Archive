---
title: "Setup of Tomcat6 on Server 10.4"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by Bartonian on 2011-05-10
Hi,
 
I have managed to setup my Server and install Tomcat (all relatively straight forward, after going through the documentation).
 
My problem is with accessing the manager webapp. I've added the additional lines to the tomcat-users.xml file in etc/tomcat6/. But for some reason I still cannot auth.
 
The users I have added have also been added to the admin group on the server (I can validate this by running the sudo command after loggin in with each username). So I am at a loss.
 
I'm sure I'm missing a simple step and will feel like a fool once it has been explained to me. But I have spent the most part of the day researching and I have to admit when I'm stuck.
 
Thanks in advance,
 
Lee

---

### Post by Bartonian on 2011-05-10
I've included my tomcat-user.xml contents, so you can check it:
 
<?xml version='1.0' encoding='utf-8'?>
<!--
  Licensed to the Apache Software Foundation (ASF) under one or more
  contributor license agreements.  See the NOTICE file distributed with
  this work for additional information regarding copyright ownership.
  The ASF licenses this file to You under the Apache License, Version 2.0
  (the "License"); you may not use this file except in compliance with
  the License.  You may obtain a copy of the License at
      [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)
  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License.
-->
<tomcat-users>
<!--
  <role rolename="tomcat"/>
  <role rolename="role1"/>
  <role rolename="manager"/>
  <role rolename="admin"/>
  <user username="tomcat" password="tomcat" roles="tomcat"/>
  <user username="both" password="tomcat" roles="tomcat,role1"/>
  <user username="role1" password="tomcat" roles="role1"/>
  <user username="mbadmin" password="fKonW2cj" roles="tomcat,role1,manager,admin"/>
  <user username="lbarton_admin" password="&bunk3r3" roles="manager,admin"/>

 
Thanks in advance

---

