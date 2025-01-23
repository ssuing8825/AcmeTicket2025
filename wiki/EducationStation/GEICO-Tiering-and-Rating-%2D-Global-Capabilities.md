# InsuranceCo Tiering and Rating - Global Capabilities

InsuranceCo Tiering and Rating (GTR) is a collection of loosely coupled, autonomous services that must work together to meet InsuranceCo&#39;s underwriting business needs. To be successful, we must define a top-level bounded context that establishes a set of cross-cutting capabilities, standards, and expectations. This bounded context is called InsuranceCo Tiering and Rating or GTR.

## Business and Technical Dimensions

GTR defines a context that consists of multiple dimensions organized around business and technical considerations.

The GTR **business dimension** is based on InsuranceCo&#39;s Tiering and Rating business domain, which is divided into subdomains consisting of business capabilities. These business capabilities are activities necessary to carry out InsuranceCo&#39;s tiering and rating business activities and consist of the business data, business processes, actors or participants, and the associated business language.

The GTR **technical dimension** consists of global and service-specific technical capabilities. The **global technical capabilities** enable the services and other parts of GTR to cooperate and interoperate to fulfill business needs in a unified and consistent manner. Examples of such shared capabilities include message contracts defining messages shared between GTR services, a GTR API that meets a targeted consumer&#39;s business needs, or a security model that makes it possible to authorize or restrict the business activities of business actors. **Service internal technical capabilities** support implementation details of services that are not collaborative. Examples of service-internal technical capabilities include data persistence, internal service communication, or tools and frameworks that support error handling, validation or business rule execution taking place within the service.

## Boundaries

The boundaries that define the GTR must not only be clearly delineated, but we must distinguish between outside entities that access the GTR through is API or through integrations.

Outside entities interacting with the GTR through **API access** must conform to our API, which will specify technical conventions (e.g. HTTP, WebSockets, etc.) and our preferred business terminology. On the other hand, if outside entities unable or unwilling to conform we must create GTR **integrations**. While these integrations are part of the GTR, they must remain separate since they contain technical and semantic elements of the external entities that should not corrupt the GTR. The GTR defines integration conventions that specify **technical integrations** be shared between all services integrating with a particular external entity while **semantic integration** (e.g., mapping of business terminology in external entities to GTR terminology and vice versa) is divided between the services responsible for the associated business capabilities that are being mapped.

## Emergent Properties and GTR Global Capabilities

In addition to enabling the cooperation needed between the services to complete meaningful business activities, the cumulative behavior of all the business and technical capabilities in the GTR will affect _how_ it performs business activities. These aggregate properties valued by our business can be thought of as _emergent properties

Examples of emergent properties relevant to GTR include performance, scalability, security, interoperability and integration, reliability, maintainability, and agility to respond quickly to changing business needs.

To fulfill InsuranceCo&#39;s business needs and to assure that GTR meets those needs effectively, we should define the following global capabilities and expectations that will apply across all the services technical capabilities that eventually become part of GTR.

### API

At this point there is not a known specific requirement for an API. However, it seems likely that a GTR API will be needed eventually. Even though individual services would implement separate capabilities a GTR API, the API must appear to external consumers as a single consistent and unified structure. The technical capabilities of the API should be consistent, as well as the terminology and language used. Other considerations such as versioning of the API should also not introduce inconsistencies.

### Messaging Backplane

We cannot assume that the services in GTR will be able to communicate freely just because technologies like Azure Service Bus and NServiceBus have been deployed. Messages must conform to consistent technical and semantic conventions, if they are to be universally understood throughout the GTR. Special attention must be paid to designing the message contracts. Because these contracts comprise the interfaces through which all GTR services communicate, they should be as stable as possible to avoid changes that would ripple throughout the GTR.

![gtr_messaging_backplane.png](/.attachments/gtr_messaging_backplane-315bf668-7f72-4604-926f-cea641758908.png)
_Figure 1: GTR Messaging Backplane with semantic and technical layers_

### Integration

- Versioning

### Entity set/definition (not domain model) (technical?)

- Domain capabilities, terms
- Used in messages
- API

### Agent model

- Actors (domain model)
- Who is authorized to do

### Other expectations

- Sync/async
- Responsiveness
  - Scale behavior (e.g. batching API)
- Failover/reliability
- Error handling/reporting

[1](#sdfootnote1anc)Emergent properties manifest themselves as the result of various system components working together, not as a property of any individual component. To put it another way, they are properties that a complex system or collection of system parts has, but which individual parts of the system do not possess.