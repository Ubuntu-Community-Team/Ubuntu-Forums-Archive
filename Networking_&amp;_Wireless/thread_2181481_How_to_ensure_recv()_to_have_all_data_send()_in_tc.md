---
title: "How to ensure recv() to have all data send() in tcp"
date: 2013-10-18
forum: Networking &amp; Wireless
---

### Post by Javed_iqbal on 2013-10-18
[COLOR=#000000][FONT=Arial]i am implementing recvall() function to get sure the data i sent completely.also i modified the send() function to sendall() like this:[/FONT][/COLOR]
int sendall (int consocket, char* buf, int* len)
 {
     int total = 0;
     int bytesleft = *len; // how many we have left to send
     int n;
     while(total < *len) {
                                    n= send(consocket, buf+total, bytesleft, 0);
                                    if (n == -1) { break; }
                                    total += n;
                                    bytesleft -= n;




                                  *len = total; // return number actually sent here
                                   return n==-1?-1:0; // return -1 on failure, 0 on success
                              }
[COLOR=#000000][FONT=Arial]}


[/FONT][/COLOR]
[TABLE]
[TR="bgcolor: transparent"]
[TD="class: postcell, bgcolor: transparent"]i am implementing recvall() function to get sure the data i sent completely.also i modified the send() function to sendall() like this:
int sendall (int consocket, char* buf, int* len)
 {
  int total = 0;
  int bytesleft = *len; // how many we have left to send
  int n;
  while(total < *len) {
                        n = send(consocket, buf+total, bytesleft, 0);
                        if (n == -1) { break; }
                        total += n;
                        bytesleft -= n;




                      *len = total; // return number actually sent here
                     return n==-1?-1:0; // return -1 on failure, 0 on success
                      }
}
How can i implement recvall() ?say i sent from server a struct of 14 bytes and i check in client to get 12 bytes..now in an unreliable situation how i should manage to get 2 bytes...i had spent time trying...any help welcomed plz


[/TD]
[/TR]
[/TABLE]

---

