FROM ubuntu:latest

RUN apt-get update && \
		apt-get install -y --no-install-recommends vsftpd db-util && \
		apt-get clean

ENV FTP_USER admin
ENV FTP_PASS admin
ENV PASV_ADDRESS REQUIRED

COPY vsftpd.conf /etc/vsftpd/
RUN rm -f /etc/vsftpd.conf
RUN ln -s /etc/vsftpd/vsftpd.conf /etc/vsftpd.conf
COPY vsftpd_virtual /etc/pam.d/
COPY run-vsftpd.sh /usr/sbin/

RUN chmod +x /usr/sbin/run-vsftpd.sh && \
		mkdir -p /var/run/vsftpd/empty

VOLUME /home/vsftpd
VOLUME /var/log/vsftpd

EXPOSE 20 21

CMD ["/usr/sbin/run-vsftpd.sh"]
