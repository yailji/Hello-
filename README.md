# Hello-
Hello!!!
#include <gtk/gtk.h>

#define _LOCALE_TO_UTF8(str) g_locale_to_utf8((const char *)(str), -1, NULL, NULL, NULL)
#define _UTF8_TO_LOCALE(str) g_locale_from_utf8((const char *)(str), -1, NULL, NULL, NULL)
#define _UTF8(str) _LOCALE_TO_UTF8((str))
#define _LOCALE(str) _UTF8_TO_LOCALE((str))
#define _U(str) _UTF8((str))
#define _L(str) _LOCALE((str)) )

void ShowLabel(GtkWidget *window)
{
    GtkWidget   *label;

    label = gtk_label_new(_U("Привет!"));
    gtk_container_add (GTK_CONTAINER (window), label);
    gtk_widget_show(label);
}

void ShowMainWindow ()
{
  GtkWidget *window;

  window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
  gtk_window_set_title (GTK_WINDOW (window), _U("Заголовок окна"));
  gtk_window_set_default_size (GTK_WINDOW (window), 400, 200);
  g_signal_connect(G_OBJECT(window), "destroy", G_CALLBACK(gtk_main_quit), NULL);

  gtk_widget_show (window);
  ShowLabel(window);
}

int main (int argc, char *argv[])
{
  gtk_init (&argc, &argv);
  ShowMainWindow ();
  gtk_main ();

  return 0;
}
