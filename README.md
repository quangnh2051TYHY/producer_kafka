# producer_kafka
Basic about send message from producer
1, run docker compose
      docker-compose up -d
2, Join ento bash of Broker
      docker-compose exec broker bash
3, Create an topic to Producer can send message
      kafka-topics --create --topic output-topic --bootstrap-server broker:9092 --replication-factor 1 --partitions 1
1, In your terminal of base project: 
      gradle shadowjar
2, Now you have an jar file after build in step 1
      java -jar build/libs/kafka-producer-application-standalone-0.0.1.jar configuration/dev.properties input.txt
3, Open zookeeper and see ouput was send in Consumer
      kafka-console-consumer --topic output-topic  --bootstrap-server broker:9092 --from-beginning --property print.key=true  --property key.separator=" : "
