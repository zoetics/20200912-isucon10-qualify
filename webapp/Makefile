restart:
	git pull
	$(MAKE) -C go isuumo
	sudo echo '' > /var/log/nginx/access.log > /var/log/nginx/error.log > /var/log/mysql/error.log
	sudo systemctl restart nginx mysql isuumo.go
.PHONY: restart

kataribe:
	sudo cat /var/log/nginx/access.log | /tmp/kataribe -f /tmp/kataribe.toml
.PHONY: kataribe

slowquery:
	sudo mysqldumpslow -s t /tmp/mysql-slow.sql
.PHONY: slowquery

pprof:
	go tool pprof -http=0.0.0.0:1080 /application/binaly/directory/ http://localhost:6060/debug/pprof/profile
.PHONY: pprof