---
title: "problem with my client using C and gtk"
date: 2015-11-14
forum: Networking &amp; Wireless
---

### Post by iggy_keke on 2015-11-14
i find a code in internet, it 's okay, but i don't understand how it do :(
```
#include <gtk/gtk.h>#include <stdio.h>
#include <string.h>   
#include <sys/socket.h> 
#include <arpa/inet.h>
#include <errno.h>


GtkWidget *window;
GtkWidget *entry;
GtkWidget *textview;
GtkWidget *button;
GtkWidget *grid;
GtkWidget *button1;


ssize_t server_socket;
ssize_t client_socket;
ssize_t new_socket;
struct sockaddr_in server;
struct sockaddr_in client;
GThread *thread=NULL;


char accept_buffer[256];
int accept_error=0;
socklen_t accept_length=0;


static void makegtk();
static void close_program(GtkWidget *widget, gpointer data);
static void translate(GtkButton *button, gpointer data);
static void server_accept();
static void server_setup(gpointer data);


int main(int argc, char *argv[])
{   
  gtk_init(&argc,&argv);
  thread=g_thread_new("t", (GThreadFunc)server_setup, NULL);
  makegtk();
  gtk_main();
  return 0;
}


static void makegtk()
{
  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  gtk_container_set_border_width(GTK_CONTAINER(window),10);
  gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
  gtk_window_set_default_size(GTK_WINDOW(window), 300, 200);
  g_signal_connect(window,"destroy",G_CALLBACK(close_program),NULL);
  grid = gtk_grid_new();
  gtk_container_add(GTK_CONTAINER(window),grid);
  entry = gtk_entry_new();
  gtk_widget_set_hexpand(entry, TRUE);
  gtk_entry_set_text(GTK_ENTRY(entry), "Client Entry");
  gtk_grid_attach(GTK_GRID(grid),entry,0,0,1,1);
  textview = gtk_text_view_new();
  gtk_text_view_set_wrap_mode(GTK_TEXT_VIEW(textview), GTK_WRAP_CHAR);
  gtk_widget_set_vexpand(textview, TRUE);
  gtk_grid_attach(GTK_GRID(grid),textview,0,1,2,1);
  button = gtk_button_new_with_label("translate");
  gtk_widget_set_hexpand(button, TRUE);
  g_signal_connect(GTK_BUTTON(button),"clicked",G_CALLBACK(translate),NULL);
  gtk_grid_attach(GTK_GRID(grid),button,0,3,1,1);
 
  gtk_widget_show_all(window);
}
static void close_program(GtkWidget *widget, gpointer data)
{
  close(server_socket);
  close(new_socket);
  g_thread_unref(thread);
  gtk_main_quit();
}
static void server_accept()
{
  memset(accept_buffer, '\0', 256*sizeof(char));
  accept_length = sizeof(client);
  new_socket=accept(server_socket, (struct sockaddr *)&client, &accept_length);
  server_accept();
}
static void translate(GtkButton *button, gpointer data)
{
  int error = 0;
  char buffer[15000];
  char *text1 = "";
  char text2[100] = "0%";
  memset(buffer, '\0', 256*sizeof(char)); 
  const char *text = gtk_entry_get_text(GTK_ENTRY(entry));
  strcat(text2,text);
  printf("%s\n",text2);
  gtk_text_buffer_set_text(gtk_text_view_get_buffer (GTK_TEXT_VIEW (textview)),text1, -1);
  client_socket = socket(AF_INET , SOCK_STREAM , 0);
  g_print("Socket Client %i\n", client_socket);
  memset(&client, 0, sizeof(client)); 
  client.sin_addr.s_addr = inet_addr("127.0.0.1");
  client.sin_family = AF_INET;
  client.sin_port = htons(5500);


  error=connect(client_socket, (struct sockaddr *)&server, sizeof(server));
  if(error<0) fprintf(stderr, "connect: %s , errno %d\n", strerror(errno), errno);
  error = write(client_socket, text2, strlen(text2));
    printf("%d\n",error);
    //note


  if(error<0) fprintf(stderr, "Write: %s , errno %d\n", strerror(errno), errno);
  
  error = read(client_socket, buffer, 15000);
  g_print("Buffer %s", buffer);
  if(error<0) fprintf(stderr, "Read: %s , errno %d\n", strerror(errno), errno);
  
  GtkTextBuffer* text_buffer = gtk_text_view_get_buffer(GTK_TEXT_VIEW(textview));
  GtkTextIter end;
  
  gtk_text_buffer_get_end_iter(text_buffer, &end);
  gtk_text_buffer_insert(text_buffer, &end, buffer, -1);
  close(client_socket);
}
static void server_setup(gpointer data)
{
  int error = 0; 
  //struct sockaddr_in server;
  server_socket = socket(AF_INET , SOCK_STREAM , 0);
  g_print("Socket Server %i\n", server_socket);
  // init info for server
  memset(&server, 0, sizeof(server)); 
  server.sin_addr.s_addr = inet_addr("127.0.0.1");
  server.sin_family = AF_INET;
  server.sin_port = htons(5500);
  // Bind the socket
  error=bind(server_socket, (struct sockaddr *)&server, sizeof(server));
  if(error<0) fprintf(stderr, "bind: %s , errno %d\n", strerror(errno), errno);
  error=listen(server_socket, 5);
  if(error<0) fprintf(stderr, "listen: %s , errno %d\n", strerror(errno), errno);
  server_accept();
}
```
the [FONT=Helvetica]server_accept and server_setup funtion, why server_accept() has recursion?
[/FONT][FONT=Helvetica] [/FONT]

---

