https://github.com/toretest/runbook-ddd-kotlin

# runbook-ddd-kotlin

A sample micro-service using DDD and a clean architecture. Implemented in Kotlin and Spring Boot.

- Domain layer is implemented in a traditional OO style (entities change its state and register domain events). 
- The domain events registration is done in the Aggregate Root (see the AggregateRoot base class), later one when the 
Application Service performs a save on the repository spring data will take care of publishing the pending events.
- Persistence implemented using Redis.

[![Build Status](https://travis-ci.org/paucls/runbook-ddd-kotlin.svg?branch=master)](https://travis-ci.org/paucls/runbook-ddd-kotlin)

## The Domain
For this sample application, we will work in an operations team domain. Our focus will be on the concept of 
a **Runbook** which tracks **Tasks**. 

A Runbook is used to track all the tasks to be completed in order for a new system deployment or maintenance operation 
to be done. Operations planner can: create a runbook for a project, add a task to the runbook, assign a task to an 
operator, reassign a task.
A task can be marked in progress only by the task assignee. An in-progress task can be completed or rejected. When all 
tasks in the runbook are completed and/or rejected, a runbook can be marked as completed.

To keep it simple, there are no dependencies between tasks thus can be completed in any order.

![Event Storming](docs/event_storming.png)

## Requirements
- Implement all use cases for the Operation planner and Operator.
- Notify operators via email when they are assigned to tasks.

## Documentation
Links to some of the articles and documentation used to implement this project:

- Implementing Domain-Driven Design, Vaughn Vernon.
- IDDD Samples https://github.com/VaughnVernon/IDDD_Samples.
- Spring - Domain event publication from aggregate roots.
https://spring.io/blog/2017/01/30/what-s-new-in-spring-data-release-ingalls#domain-event-publication-from-aggregate-roots
- Building web applications with Spring Boot and Kotlin https://spring.io/guides/tutorials/spring-boot-kotlin/
- Retrieve User Information in Spring Security http://www.baeldung.com/get-user-in-spring-security
- Configure Redis: 
http://www.baeldung.com/spring-data-redis-tutorial
https://docs.spring.io/spring-data/redis/docs/2.0.7.RELEASE/reference/html/#get-started
https://github.com/spring-projects/spring-data-examples/tree/master/redis/repositories

## TODO
- Improve domain description: A new task can be assigned or unassigned, an unassigned task can no be marked in progress.