### **SHAKHRIYOR ERGASHEV**

:globe_with_meridians: Innopolis, Russian Federation  
:e-mail: **E-mail**: shahriyor.ergashev@gmail.com  
:desktop_computer: **Skype**: shaxri77  
:calling: **Phone**: +79274219171
<br>
<br>

#### **SUMMARY**

> I have 4+ years of Backend, Web Development experience as a Java / Scala Software Engineer with a focus on APIs and micro-services. I specialize in building high load, data driven, feature rich Enterprise Web Applications. In spare time, i build my own scalable, distributed systems, swim and praise my daughter for her dance skills on the stage. Highlights of my soft skills are Team Worker, Responsible, Proactive, Quick-learner, Positive thinker.

#### :briefcase: **WORK EXPERIENCE**

**Portavita LLC**, Innopolis, Russian Federation August, 2019 - currently  
Examples of main works done as **Software Engineer**:<br>

- Patient Assistant App – Single Page Web Application <br>which helps patients with anticoagulation treatment
- Personal Health Data Environment – Hub of Medical data entered by General Practitioners.

:hammer_and_wrench: **Technologies**:

- _Scala, Java;_
- _Apache Kafka;_
- _Jenkins;_
- _jUnit, xUnit, Scalatest, Easymock, Mockito;_
- _PostgreSQL;_
- _AkkaHTTP;_
- _Jira, Fisheye/Crucible and Git;_
- _Docker, Kubernetes and Helm;_
- _Linux/Ubuntu._

:bookmark_tabs: **Standards**:

- HL7 V2&3,
- SNOMED CT,
- FHIR DTSU 2, STU 3 & R4.

:test_tube: **Methodologies**:

- Scrum

_Code example extraction_:

```
package com.innochildren.routes

import akka.actor.ActorRef
import akka.http.scaladsl.marshallers.sprayjson.SprayJsonSupport._
import akka.http.scaladsl.server.Directives._
import akka.http.scaladsl.server.Route
import akka.pattern._
import akka.util.Timeout
import com.innochildren.actors.PostActor.{ AddPost, DeletePost, GetPostById, GetPosts, UpdatePost }
import com.innochildren.actors.SchoolActor._
import com.innochildren.mappings.JsonMappings
import com.innochildren.models.Types.Id
import com.innochildren.models.{ Post, School }
import spray.json._

import scala.concurrent.ExecutionContext.Implicits.global
import scala.concurrent.duration._

trait PostRoute extends JsonMappings {
  def postActor: ActorRef

  implicit lazy val timeoutPostActor: Timeout = Timeout(5.seconds)

  val postApi: Route =
    (path("posts") & get) {
      val res = (postActor ? GetPosts("all")).mapTo[Seq[Post]].map(_.toJson)
      complete(res)
    } ~
      (path("posts" / ".+".r) & get) { id =>
        val res = (postActor ? GetPostById(id)).mapTo[Post].map(_.toJson)
        complete(res)
      } ~
      (path("posts") & post) {
        entity(as[Post]) { post =>
          val res = (postActor ? AddPost(post)).mapTo[Id]
          complete(res)
        }
      } ~
      (path("posts" / ".+".r) & put) { id =>
        entity(as[Post]) { post =>
          val res = (postActor ? UpdatePost(post, id)).mapTo[Int].map(_.toJson)
          complete(res)
        }
      } ~
      (path("posts" / ".+".r) & delete) { id =>
        val res = (postActor ? DeletePost(id)).mapTo[Int].map(_.toJson)
        complete(res)
      }
}
```

**LTD STARTSOFT**, Tashkent, Uzbekistan August, August, 2016 – June, 2018  
Examples of main works done as **Software Developer**:<br>

- Single electronic archive system of civil status records
- Authority of the prosecutor
- Executory process automation system of the Department of Execution of Court Decisions

:hammer_and_wrench: **Technologies**:

- _Java 8, Java2EE, Spring (Cloud, Security, JPA, Boot, Web, REST);_
- _PostgreSQL;_
- _JBoss;_
- _JSF CDI;_
- _Hibernate;_
- _Git;_
- _Jira Atlassian;_
- _Maven;_
- _Microservices, AWS, Docker, Jenkins;_
- _Angular JS, JUnit/Mockito;_
- _JSP, HTML/CSS;_

:test_tube: **Methodologies**:

- Adopted Scrum

#### :man_student: **EDUCATION**

- Innopolis University, Republic of Tatarstan, Russian Federation

  > Master of Science in Information Technology – Software Engineering
  > <br>**Thesis work**:
  > Design and implementation of a system for enterprise tax and reliability management using agile methodologies.

- Turin Polytechnic University in Tashkent, Uzbekistan
  > Bachelor of Science Information Technology and ACS in the industry
  > <br>**Thesis work**:
  > Health Technology Management’s Open Source Information System Implementation at pilot project.

#### :man_technologist: **ADDITIONAL TRAININGS**

- Apache Kafka, Kafka Streams, Akka HTTP, Akka Streams | 2019
- PL/SQL, Oracle Developer, SPRING MVC, GWT, ASP.NET CORE, ASP.NET MVC, Angular | 2016
- IBM SPSS Statistics, JQuery, Bootstrap | 2015
- Learn German at the Goethe Institute, A-2,2 level | 2014
- Programming languages C, Java, Scala, PHP, JavaScript | 2012

#### :capital_abcd: **LANGUAGE SKILLS**

- Uzbek (native) :star::star::star::star::star:,
- Russian (fluent) :star::star::star::star:,
- English (fluent) :star::star::star::star:,
- Italian(Foundation) :star:,
- German A2 :star::star:
