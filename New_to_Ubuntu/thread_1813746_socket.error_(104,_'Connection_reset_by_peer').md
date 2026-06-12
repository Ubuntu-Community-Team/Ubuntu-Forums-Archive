---
title: "socket.error: (104, 'Connection reset by peer')"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by r.g.babukarthik on 2011-07-28
can anyone please help when i try to connect, getting the error


[root@localhost python]# python migration.py
(104, 'Connection reset by peer')
Traceback (most recent call last):
  File "migration.py", line 6, in ?
    session.xenapi.login_with_password("root","karthik")
  File "/usr/lib/python2.4/site-packages/XenAPI.py", line 229, in __call__
    return self.__send(self.__name, args)
  File "/usr/lib/python2.4/site-packages/XenAPI.py", line 124, in xenapi_request
    self._login(methodname, params)
  File "/usr/lib/python2.4/site-packages/XenAPI.py", line 148, in _login
    result = _parse_result(getattr(self, 'session.%s' % method)(*params))
  File "/usr/lib/python2.4/xmlrpclib.py", line 1096, in __call__
    return self.__send(self.__name, args)
  File "/usr/lib/python2.4/xmlrpclib.py", line 1383, in __request
    verbose=self.__verbose
  File "/usr/lib/python2.4/xmlrpclib.py", line 1131, in request
    errcode, errmsg, headers = h.getreply()
 File "/usr/lib/python2.4/httplib.py", line 1143, in getreply
    response = self._conn.getresponse()
  File "/usr/lib/python2.4/httplib.py", line 872, in getresponse
    response.begin()
  File "/usr/lib/python2.4/httplib.py", line 336, in begin
    version, status, reason = self._read_status()
  File "/usr/lib/python2.4/httplib.py", line 294, in _read_status
    line = self.fp.readline()
  File "/usr/lib/python2.4/socket.py", line 325, in readline
    data = recv(1)
socket.error: (104, 'Connection reset by peer')

---

